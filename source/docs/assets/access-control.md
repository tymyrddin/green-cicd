# Access control

Access controls grant or deny access to resources and systems inside and outside the execution 
environment. Pipeline execution nodes use these to perform various actions. 

If malicious code enters the pipeline, adversaries can exploit misconfigured access control or access control 
vulnerabilities to abuse pipeline permissions to move laterally in or outside the CI/CD system.

## Mitigations

* Use CI server contexts to limit which jobs can be executed by whom.