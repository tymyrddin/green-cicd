# Usage of third party services

CI/CD pipelines often use third-party integrations because they facilitate rapid development and delivery. 

Improper usage of third parties can introduce security weaknesses into the pipeline. 

## Mitigations

Securing usage of third-party services involves implementing controls that achieve governance and visibility, such as role-based access controls.

* Set up branch protection to prohibit team members from pushing code directly to that branch, and instead force all changes to go through the pull request (PR) process. 
* Set up security groups like `development-leads` and `delivery-managers`. All developers can push to their own branches and issue pull requests, but only team leaders can approve changes to be merged into the protected main branch, and only delivery managers can give the green light to trigger releases of software.
* Use CI server contexts to limit which jobs can be executed by whom.