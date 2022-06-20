# Source code management access control

Everything that takes part in the application lifecycle is checked into source control: Source code, build 
scripts, pipeline definition, configuration values, tests and test data, database schemas, database update scripts, 
infrastructure definition scripts, cleanup/installation/purging scripts, and associated documentation.

Anybody with access can check out everything that relates to an application and can recreate it locally or in any other 
alternative environment. ANY CI/CD solution can probably be compromised if an attacker has access to the source code.

Source stage (Commit stage) is where new features and new code are integrated with the base code. 
It can trigger the CI/CD pipeline by changes to the code repository, user-initiated workflows, and automated schedules.
