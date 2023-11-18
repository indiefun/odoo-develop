FROM mcr.microsoft.com/devcontainers/python:3.10-bullseye

ENV PYTHONUNBUFFERED 1

RUN apt-get update \
    && apt-get install -y python3-pip libldap2-dev libpq-dev libsasl2-dev \
    && apt-get install -y ca-certificates curl gnupg xz-utils \
    && apt-get install -y fonts-noto-cjk \
    && apt-get install -y postgresql-client \
    && rm -rf /var/lib/apt/lists/*

RUN curl -o wkhtmltox.deb -sSL https://github.com/wkhtmltopdf/packaging/releases/download/0.12.6.1-3/wkhtmltox_0.12.6.1-3.bullseye_amd64.deb \
    && apt-get update \
    && apt-get install -y --no-install-recommends ./wkhtmltox.deb \
    && rm -rf /var/lib/apt/lists/* wkhtmltox.deb

ARG NODE_MAJOR=20
RUN mkdir -p /etc/apt/keyrings \
    && curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg \
    && echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_${NODE_MAJOR}.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list \
    && apt-get update && sudo apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*
RUN npm install --global rtlcss

ARG ODOO_VERSION=16.0
RUN curl -fsSLO https://raw.githubusercontent.com/odoo/odoo/${ODOO_VERSION}/requirements.txt \
    && pip3 install -r requirements.txt \
    && rm -f requirements.txt
