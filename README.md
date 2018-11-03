# docker-kubectl
https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl
## kubectl tool in docker
```
FROM alpine:3.8
ENV KUBECTL_VERSION v1.12.0
RUN apk add --no-cache curl; \
    curl -LO https://storage.googleapis.com/kubernetes-release/release/$KUBECTL_VERSION/bin/linux/amd64/kubectl; \
    chmod +x ./kubectl; \
    mv ./kubectl /usr/local/bin/
```
```
docker build -t ferrariche/kubectl:1.12.0-apline .
```
## Build your own docker kubectl
Dockerfile
```
FROM ferrariche/kubectl:1.12.0-apline
RUN mkdir -p /root/.kube
ADD ./config /root/.kube/config
```
