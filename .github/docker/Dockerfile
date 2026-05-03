FROM node:20-slim

# git is required by sgd to walk commit history
RUN apt-get update \
    && apt-get install -y --no-install-recommends git \
    && rm -rf /var/lib/apt/lists/*

# Pinned SF CLI version — matches the team's agreed-upon version
RUN npm install --global @salesforce/cli@2.113.6

# Install sgd as an sf CLI plugin (not as a standalone npm package)
RUN echo 'y' | sf plugins install sfdx-git-delta

# Verify everything is wired up correctly at build time.
# If any of these fail, the image won't build — fail fast.
RUN sf version \
    && sf plugins \
    && sf sgd source delta --help > /dev/null