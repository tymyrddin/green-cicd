# Infrastructure code workflows

An overview of the background info, design, and implementation of a production-ready CI/CD pipeline for infrastructure 
code.

## Assumptions

Assuming trunk based development:

*   Small, frequent commits reduce the scope of each integration
*   Automated testing
*   Feature toggles

And two types of infrastructure code:

*   Infrastructure Modules for deploying specific components of the infrastructure, such as Virtual Private Clouds (VPCs), databases, and docker clusters like Elastic Container Service, Kubernetes, Nomad, etc.
*   Live infrastructure configurations, specific parameters for each component in the infrastructure architecture, the front-end for its deployments.

Typically, these two different types of infrastructure code have separate repositories, an infrastructure-modules 
repository for modules and infrastructure-live repository for live configuration. This makes it easier to test module 
code, promote immutable versions across environments, and keep it DRY ("Don't repeat yourself"). There are distinct differences in the way the code is tested, used, and deployed between the two types of infrastructure 
code.

## Cloning and branching

The first step in making changes to a code base is to clone the repository locally and begin development on a new 
branch. Using git:

    git clone $REPO_URL
    git checkout -b $NEW_BRANCH_NAME

## Running code locally

With infrastructure modules, this involves deploying the module in a sandbox environment, because checking whether 
infrastructure code works requires making the actual API calls to the cloud to deploy it. For example, to test a 
Terraform module, define example code that sets up the necessary resource dependencies that the module needs, and then 
deploy that into a sandbox with `terraform apply`. Then inspect the deployed resources to make sure they are 
functioning as expected. These processes can be captured in an automated test.

Locally testing live infrastructure is more difficult because the code is tied to a specific live environment (the 
configuration to manage live infrastructure). The only real test possible for live infrastructure config is a dry run 
of the infrastructure code. Most Infrastructure as Code tools support such dry runs of the code to check what it would 
do against the existing environment. For example, with Terraform, it is possible to run `terraform plan` to sanity 
check the planned actions Terraform will take. The trunk should be a true reflection of the live environment, so 
expect there to be no changes to make on a fresh clone of trunk.

## Making code changes

Testing infrastructure modules can take a long time because it requires deploying infrastructure (on 10-20 minutes). 
There may be ways to improve the test cycles for infrastructure modules.

Testing live infrastructure config can be done in minutes (because it only involves doing a dry run). 

## Pull (Merge) requests and reviews

Focus the review process on things that are hard to check through automated testing, such as checking security flaws, 
reviewing general code design, enforcing style guides, or identifying potential performance issues on larger data sets.

## Running automated tests

The CI server can run automated tests for infrastructure modules. Tests for infrastructure modules can take a long 
time to run (costly). Run the tests only for the modules that changed instead of doing a regression test for all the 
modules on every commit. Run a nightly build that runs the whole suite on a regular interval that is less frequent than 
developers updating the code. 

For live infrastructure config, the CI server can perform a dry run of the infrastructure and post the entire log of 
the run for further analysis. This has potential security issues as the logs for a dry run would typically include 
secrets. Encrypt the results before it is posted and guard who has access.

## Merging and releasing

After merging the code into trunk, a new, immutable, versioned release artifact can be generated that can be deployed.

Infrastructure modules are usually consumed as a library. Most infrastructure as code tools consume the libraries 
directly from a Git repository. Use a Git tag to mark a revision with a human friendly name to generate the release 
artifact.

For live infrastructure config, there is usually no release artifact.

## Deploying

To deploy infrastructure modules, references to the modules in the live infrastructure config need to be created or 
updated. If the module is already deployed, this may be as simple as bumping the ref tag in the live config. If the 
module is being deployed for the first time, then this will require creating a new configuration in the live 
infrastructure config to deploy the module. 

An automated deployment of infrastructure modules may be risky as a simple change could destroy the database. 
But, sometimes it is not practical to manually roll out deployments even for infrastructure modules. In some 
cases manual roll out can be more risky from a security perspective (like increasing attack surface by passing out 
admin credentials to all developers). Human verification to the automated steps of the workflow can be
used. 

For live infrastructure config, deploying the code is applying the code to the live environment and is
highly dependent on the tool. For example, `terraform apply` or `kubectl apply`. 

What needs automating depends on the nature of the change. The pipeline differs based on which 
configurations were updated.