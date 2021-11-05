FROM google/cloud-sdk:alpine
#RUN apt-get -y update \
ENV TZ=America/New_York
RUN apk update && apk upgrade \
 && apk add --update curl tzdata openssl \
 && apk add ca-certificates \
 && gcloud components install beta -q \
 && curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl \
 && chmod +x ./kubectl \
 && mv ./kubectl /usr/local/bin/kubectl \
 && curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > /tmp/get_helm.sh \
 && chmod 700 /tmp/get_helm.sh && ./tmp/get_helm.sh && helm init -c
 # Clean APK cache
 RUN rm -rf /var/cache/apk/*