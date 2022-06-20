# Source code

Creating source code is the first phase in a CI/CD pipeline. During this phase, developers translate requirements into 
algorithms, features, and behaviours. Tools vary and depend on purpose and language of project, developer preferences
and other variables. There is no uniform source creation pipeline. 

A source code creation pipeline may incorporate any of the following:

* A programming framework, such as Python or JavaScript.
* An integrated development environment (IDE) such as PyCharm or Codium. 
* Testing tools such as Jest for JavaScript or pytest for Python programs. 
* Code-quality tools, such as black, mypy, flake8, isort, and vulnerability scanners. 
* Code repositories and version control systems, such as Git.

ANY CI/CD solution can probably be compromised if an attacker has access to the source code.

Source stage (Commit stage) is where new features and new code are integrated with the base code. 
It can trigger the CI/CD pipeline by changes to the code repository, user-initiated workflows, and automated schedules. 