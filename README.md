# Task 2: Simple Jenkins Pipeline for CI/CD

Elevate Labs DevOps Internship, Task 2.

A declarative Jenkins pipeline (`Jenkinsfile`) that builds, tests and deploys a Dockerized Node.js app. Jenkins checks the repo for new commits (Poll SCM) and runs the pipeline automatically.

## Stages
1. **Build**: builds the Docker image
2. **Test**: runs `npm test` inside the image
3. **Deploy**: starts the container on port 3000 and checks the app responds

## Files
- `Jenkinsfile`: the pipeline
- `jenkins/Dockerfile`: Jenkins image with the Docker CLI added
- `app.js`, `test/`, `Dockerfile`: the Node.js app

*Setup steps and screenshots coming soon .*
