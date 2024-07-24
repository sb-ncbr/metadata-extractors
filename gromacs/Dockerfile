FROM gromacs/gromacs:latest

RUN apt-get update && apt-get install -y \
    python3 \
    && rm -rf /var/lib/apt/lists/*

COPY . /opt/gmx-dump

ENV PATH $PATH:/opt/gmx-dump

USER 1000

WORKDIR /data
