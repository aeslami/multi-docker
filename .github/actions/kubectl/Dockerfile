FROM gcr.io/cloud-builders/kubectl

RUN cat $HOME/.kube/config
COPY entrypoint.sh /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
CMD ["help"]
