FROM topiaruss/dreambase

# better to use COPY than ADD
COPY scripts/* /scripts


# in a descendant, you can override ENTRYPOINT and CMD, or CMD [] to have none
CMD ["scripts/bye.sh"]