# Automation-git-TO-DockerHub

# Dockerfiles

## Why?

This repository serves as a central hub for organizing all our Docker images. We have two workflows to automate the process:

1. [weekly-build-image.yml](./.github/workflows/weekly-build-image.yml): This weekly workflow builds and updates images on Dockerhub.
2. `<image-name>.yml`: This workflow, triggered by changes in a specific image subdirectory, automatically builds and updates the corresponding image.
   - [Example Workflow](./.github/workflows/ubantu-image.yml)

## How can I automate my image?

1. Create a repository on Dockerhub.
2. Generate a new directory with the exact name of your image.
   - Inside the directory, include the `Dockerfile` and its dependencies.
   
   Directory structure example:
   ```plaintext
   image_name
   ├── Dockerfile
   ├── Dependency
   ├── Dependency

### Please refer to pre-existing image directories if you have any questions.
