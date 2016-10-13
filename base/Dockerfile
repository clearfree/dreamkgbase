FROM ubuntu

# better to use COPY than ADD
COPY scripts /scripts
RUN date > created


# in a descendant, you can override ENTRYPOINT and CMD
ENTRYPOINT ["bin/bash"]
CMD ["scripts/ident.sh"]