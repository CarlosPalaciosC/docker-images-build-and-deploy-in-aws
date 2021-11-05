# Dockerfiles with tools installed in aws-cli and gcloud-cli

- These images were created to be used in continuous integration and delivery server.

- aws-cli/alpine/Dockerfile: (Use this image Just for development)

  - Alpine 3.11
  - kubectl (last version)
  - helm 2.0
  - aws cli (last version 2.x) (From multistage build)
  - aws ecs (last version)

- aws-cli/android/Dockerfile:

  - aws cli (last version 2.x)
  - android-30

- aws-cli/maven/Dockerfile:

  - maven:3.6.3-jdk-8
  - kubectl (last version)
  - helm 2.0
  - aws cli (last version 2.x) (From multistage build)
  - aws ecs (last version)

- aws-cli/node/Dockerfile:

  - node:10.15.3
  - kubectl (last version)
  - helm 2.0
  - aws cli (last version 2.x) (From multistage build)
  - aws ecs (last version)

- gcloud-cli/gcloud-sdk/Dockerfile:

  - google/cloud-sdk:alpine
  - kubectl (last version)
  - helm 2.0

- gcloud-cli/maven/Dockerfile:

  - maven:3.6.3-jdk-8
  - gcloud-sdk (last version)
  - helm 2.0
  - kubectl (last version)
  - docker-ce
