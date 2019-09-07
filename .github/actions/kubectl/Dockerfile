FROM gcr.io/cloud-builders/kubectl

RUN cat /github/home/.kube/config
COPY entrypoint.sh /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
CMD ["help"]
