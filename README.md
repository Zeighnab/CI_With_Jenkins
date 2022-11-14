# Continous Integration with Jenkins

This project demonstrate building and testing application, and storing storing the artifact using jenkins pipeline as a code.

## Tools employed are:
1. Maven/OracleJDK - for builds
2. Sonarqube - for Code Analysis i.e to check for any vulnerablities and standards
3. Nexus - for storing artifacts(softwares)

## Pipeline As A Code

* Automate pipeline setup with `Jenkinsfile`
* Jenkinsfile defines Stages in CI/CD Pipeline
* Jenkinsfile is a text file with Pipeline DSL Syntax
* It has two syntax; Scripted and Declarative