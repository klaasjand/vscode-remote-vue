FROM node:16.17.0-bullseye-slim
LABEL maintainer="Klaas Jan Dijksterhuis"

ARG USERNAME=node
ARG NPM_GLOBAL=/home/$USERNAME/.local

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        curl \
        git

# Remove or comment out to use root user
USER $USERNAME

RUN mkdir -p ${NPM_GLOBAL}/bin \
    && echo "export PATH=$NPM_GLOBAL/bin/:$PATH" >> ~/.bashrc \
    && npm config set prefix ${NPM_GLOBAL} \
    && npm install -g eslint create-vue@latest
