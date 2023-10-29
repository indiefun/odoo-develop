FROM mcr.microsoft.com/devcontainers/python:3.10-bullseye

ENV PYTHONUNBUFFERED 1

RUN apt-get update \
    && apt-get install -y python3-pip libldap2-dev libpq-dev libsasl2-dev wkhtmltopdf \
    && apt-get install -y ca-certificates curl gnupg \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /workspaces
WORKDIR /workspaces

ARG ODOO_VERSION=16.0
RUN git clone -b ${ODOO_VERSION} --single-branch --depth=1 https://github.com/odoo/odoo.git odoo
RUN pip3 install -r odoo/requirements.txt

ARG NODE_MAJOR=20
RUN mkdir -p /etc/apt/keyrings \
    && curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg \
    && echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_${NODE_MAJOR}.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list \
    && apt-get update && sudo apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*
RUN npm install --global rtlcss
