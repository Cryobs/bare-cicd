# bare CI/CD
A minimal, self-hosted CI/CD template that lives **inside your repository** and can be executed locally or on a server without relying on external CI providers.
## Problem
Most modern CI/CD solutions (GitHub Actions, GitLab CI, Jenkins, etc.) are powerful but often overkill for small projects or self-hosted servers.

Common issues:
- CI/CD logic is tightly coupled to a specific platform
- Pipelines are hard to test locally
- Small changes require commits just to validate the pipeline
- CI systems consume significant server resources
- Not practical for weak or low-power servers (VPS, Raspberry Pi, homelabs)

For lightweight infrastructure, running a full CI/CD platform often makes no sense.

## Idea

`bare-cicd` treats CI/CD as **plain project code**, not a separate platform.

The main ideas are:
- CI/CD scripts live inside the repository
- The pipeline can be executed locally from the `cicd/` directory
- No need to SSH into the server to change tests or deployment logic
- Minimal CPU and memory usage
- Git is used as a trigger, not as a CI provider

This approach is designed for **simple, transparent and resource-efficient deployments**.


## How it works

The pipeline follows a classic structure:

`test -> deploy`

Each step is a simple script.
You can run them:
- Locally (for testing and debugging)
- On a server (for real deployment)

The same scripts are used everywhere - no special CI environment.

## Pipeline structure
```
cicd/
├── test.sh
├── build.sh
├── deploy.sh
```

## Usage
1. Make on your server a bare repository (here [tutorial](https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server))
2. Clone that repo to your bare repo, in hooks
   
DONE!

Now you can push to your server and server will test your code and deploy with your scripts in `cicd/`
