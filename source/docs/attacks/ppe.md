# Poisoned pipeline execution

Poisoned pipeline execution (PPE) is a technique that enables adversaries to poison the CI pipeline. 

The technique abuses permissions in [source code management (SCM)](../assets/scm-access.md) repositories to manipulate the 
build process. It involves injecting malicious code or commands into the build pipeline configuration, poisoning the 
pipeline to run malicious code during the build process.

## Articles

* [PPE — Poisoned Pipeline Execution: Running malicious code in your CI, without access to your CI](https://medium.com/cider-sec/ppe-poisoned-pipeline-execution-34f4e8d0d4e9)