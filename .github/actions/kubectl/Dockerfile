FROM gcr.io/cloud-builders/kubectl

COPY entrypoint.sh /entrypoint.sh
RUN cat $HOME/.kube/config

ENTRYPOINT ["/entrypoint.sh"]
CMD ["help"]
