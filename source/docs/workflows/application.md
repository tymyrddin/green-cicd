# Application code workflow

An overview of the background info, design, and implementation of a production-ready CI/CD pipeline for application 
code.

## Assumptions

Assuming trunk based development:

*   Small, frequent commits reduce the scope of each integration
*   Automated testing
*   Feature toggles

Most code will go through this workflow:

## Clone and branch

The first step in making changes to a code base is to clone the repository locally and begin development on a new 
branch. Using git:

    git clone $REPO_URL
    git checkout -b $NEW_BRANCH_NAME

## Running code locally

To run the code locally to sanity check the current state of trunk (to be clean and unbroken), spin up a local 
environment for the application code to test it out. For a simple web server written in a general purpose programming 
language, run the server code to bring up a local copy of the application and manually test it by loading the web 
server in the browser. Or, run the automated test suite associated with the application.

## Making code changes