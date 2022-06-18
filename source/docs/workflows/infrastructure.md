# Infrastructure code workflow

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

If modules are "blueprints" then the live configuration are the "houses" built using the "blueprints." Each "house" may have slightly different features or customisation, even though they share a common blueprint.

Typically, these two different types of infrastructure code have separate repositories, an infrastructure-modules 
repository for modules and infrastructure-live repository for live configuration. This makes it easier to test module 
code, promote immutable versions across environments, and keep it DRY ("Don't repeat yourself").

There are distinct differences in the way the code is tested, used, and deployed between the two types of infrastructure 
code.

Most code will go through a workflow like this:

## Clone and branch

The first step in making changes to a code base is to clone the repository locally and begin development on a new branch. Using git:

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