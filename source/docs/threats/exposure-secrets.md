# Exposure of secrets

CI/CD tools consume numerous secrets to gain access to sensitive resources, such as [databases](../assets/database.md) 
and [codebases](../assets/source-code.md). 

Secrets are required for authentication between tools and also participate in the build and deployment process to ensure 
deployed resources have access. 

The increasing consumption of secrets by CI/CD pipelines introduces complexities, making it difficult to store, 
transmit, and audit secrets securely.