FROM ubuntu:14.04

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8

RUN apt-get update --fix-missing && \
    apt-get install -y wget bzip2 ca-certificates \
    libglib2.0-0 libxext6 libsm6 libxrender1 git gcc

RUN echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh
RUN wget --quiet \
    https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh
ENV PATH /opt/conda/bin:$PATH

# take a first pass at creating the environment, but without the code repos
COPY environment.yml /home/

RUN echo 'creating conda env' && \
    cd /home && conda env create --name dreamkg_docker --force

# Insert useful scripts, and timestamp the build
COPY scripts /scripts
RUN date > created

ENTRYPOINT ["/bin/bash", "-c"]
CMD ["scripts/ident.sh"]
