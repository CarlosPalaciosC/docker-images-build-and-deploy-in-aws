FROM maven:3.6.3-jdk-8

ENV TZ=America/New_York

RUN apt-get -y update \
 && apt-get -y install apt-transport-https gnupg2 software-properties-common apt-utils lsb-release dirmngr \
 && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
 && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" \
 && export CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)" \
 && echo "deb http://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list \
 && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 93C4A3FD7BB9C367 \
 && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - \
 && echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | tee -a /etc/apt/sources.list.d/kubernetes.list \
 && curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > /tmp/get_helm.sh \
 && chmod 700 /tmp/get_helm.sh && ./tmp/get_helm.sh && helm init -c \
 && apt-get -y update \
 && apt-get -y install docker-ce google-cloud-sdk kubectl \
 && apt-get -y upgrade \
 && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone