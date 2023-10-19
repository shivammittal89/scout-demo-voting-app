FROM python:3.9-slim@sha256:86d569ea8a3e1ebd34f21987ff0d187a8eaf5a8cc47803e1e69e1fb83ff987b2

# add apache bench (ab) tool
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    apache2-utils \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /seed

COPY . .

# create POST data files with ab friendly formats
RUN python make-data.py

CMD /seed/generate-votes.sh