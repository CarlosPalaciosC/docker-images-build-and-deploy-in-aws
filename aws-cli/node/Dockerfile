FROM amazonlinux:2 as installer
RUN yum update -y \
    && yum install -y unzip \
    && curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscli-exe-linux-x86_64.zip" \
    && unzip awscli-exe-linux-x86_64.zip \
    && ./aws/install --bin-dir /aws-cli-bin/

FROM node:10.15.3
ARG DEBIAN_FRONTEND=noninteractive
ARG GLIBC_VER=2.31-r0
RUN apt-get update && apt-get install -y binutils openssl git \
    curl bash jq groff unzip \
    && curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl \
    && chmod +x ./kubectl \
    && mv ./kubectl /usr/local/bin/kubectl \
    && curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > /tmp/get_helm.sh \
    && chmod 700 /tmp/get_helm.sh && ./tmp/get_helm.sh && helm init -c \
    && curl -o /usr/local/bin/ecs-cli https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-linux-amd64-latest \
    && curl -o ecs-cli.asc https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-linux-amd64-latest.asc \
    && chmod +x /usr/local/bin/ecs-cli

COPY --from=installer /usr/local/aws-cli/ /usr/local/aws-cli/
COPY --from=installer /aws-cli-bin/ /usr/local/bin/