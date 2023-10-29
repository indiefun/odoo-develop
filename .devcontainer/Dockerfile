FROM mcr.microsoft.com/devcontainers/python:3.10-bullseye

ENV PYTHONUNBUFFERED 1

RUN apt-get update \
    && apt-get install -y python3-pip libldap2-dev libpq-dev libsasl2-dev wkhtmltopdf \
    && apt-get install -y ca-certificates curl gnupg \
    && rm -rf /var/lib/apt/lists/*

ARG NODE_MAJOR=20
RUN mkdir -p /etc/apt/keyrings \
    && curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg \
    && echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_${NODE_MAJOR}.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list \
    && apt-get update && sudo apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*
RUN npm install --global rtlcss

ARG ODOO_VERSION=16.0
RUN curl -fsSLO https://raw.githubusercontent.com/odoo/odoo/16.0/requirements.txt \
    && pip3 install -r requirements.txt \
    && rm -f requirements.txt

RUN mkdir -p /workspaces && chown vscode:vscode /workspaces
WORKDIR /workspaces
USER vscode

RUN git clone -b ${ODOO_VERSION} --single-branch --depth=1 https://github.com/odoo/odoo.git /workspaces/odoo
