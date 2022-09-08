FROM node:16.17.0-bullseye-slim
LABEL maintainer="Klaas Jan Dijksterhuis"

ARG USERNAME=node
ARG NPM_GLOBAL=/usr/local/share/npm
ENV PATH=${NPM_GLOBAL}/bin:${PATH}

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        sudo \
        curl \
        git

# Configure npm and make sure $USERNAME can install global packages. This may
# cause errors when certain scaffolding tools try to install global packages.
# Solve this by installing them manually.
RUN mkdir -p ${NPM_GLOBAL} \
    && touch /usr/local/etc/npmrc \
    && npm config -g set prefix ${NPM_GLOBAL} \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Remove or comment out to use root user
USER $USERNAME

RUN sudo npm install -g eslint create-vue@latest
