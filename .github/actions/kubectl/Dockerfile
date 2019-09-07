FROM alpine:3.5 as doctl

ENV DOCTL_VERSION=1.22.0
ENV DOCTL_SHA256=5817d5c397e49e9d4b025e95d5a161b4200631ff68a4a1bbda618a3261d717a2

RUN apk add --no-cache curl

RUN mkdir /lib64 && ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2

RUN curl -L https://github.com/digitalocean/doctl/releases/download/v${DOCTL_VERSION}/doctl-${DOCTL_VERSION}-linux-amd64.tar.gz  | tar xz -C /usr/local/bin/

RUN /bin/echo "${DOCTL_SHA256}  /usr/local/bin/doctl" | sha256sum -c -

RUN "doctl kubernetes cluster kubeconfig save ${CLUSTER_NAME}"

FROM gcr.io/cloud-builders/kubectl

COPY --from=doctl $HOME/.kube/config $HOME/.kube/config
COPY entrypoint.sh /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
CMD ["help"]
