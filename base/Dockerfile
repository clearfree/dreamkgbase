FROM ubuntu:14.04

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8

RUN apt-get update --fix-missing && \
    apt-get install -y \
    bzip2 \
    ca-certificates \
    gcc \
    git \
    libfreeimage-dev \
    libfreeimage3 \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender1 \
    wget && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/

RUN echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh
RUN wget --quiet \
    https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh
ENV PATH /opt/conda/bin:$PATH

COPY environment.yml /home/

RUN echo 'create conda env, clean' && \
    cd /home && conda env create --name dreamkg_docker --force

# I think conda clean was removing pytest related components.
# && \
# conda clean -ay

# Insert useful scripts, and timestamp the build
COPY scripts /scripts

RUN echo "base created " > /created_base.txt && \
    date >> /created_base.txt

ENTRYPOINT ["/bin/bash", "-c"]
CMD ["/scripts/ident.sh"]
