FROM node:20-slim

RUN apt-get update \
    && apt-get install -y --no-install-recommends git ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN npm install --global @salesforce/cli@2.113.6

RUN echo 'y' | sf plugins install sfdx-git-delta

RUN sf version \
    && sf plugins \
    && sf sgd source delta --help > /dev/null