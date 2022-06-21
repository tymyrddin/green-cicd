# Exposure of secrets

CI/CD tools consume numerous secrets (authentication credentials, like passwords and API tokens) to gain access to 
services and applications, such as [databases](../assets/database.md) and [codebases](../assets/source-code.md).

Threats:

* Hardcoding of identity and access management key pairs within an (internal) repository 
* Making every repository within the environment accessible to any of the organization’s developer accounts

## Mitigations

Securing usage of third-party services involves implementing controls that achieve governance and visibility, such as role-based access controls.

* Set up branch protection to prohibit team members from pushing code directly to that branch, and instead force all changes to go through the pull request (PR) process. 
* Set up security groups like `development-leads` and `delivery-managers`. All developers can push to their own branches and issue pull requests, but only team leaders can approve changes to be merged into the protected main branch, and only delivery managers can give the green light to trigger releases of software.
* Use CI server contexts to limit which jobs can be executed by whom.
* If using AWS, use Amazon GuardDuty, an AWS security tool that monitors AWS accounts for malicious activity

