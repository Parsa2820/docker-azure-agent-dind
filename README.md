# docker-azure-agent-dind-offline
[![Docker](https://github.com/Parsa2820/docker-azure-agent-dind/actions/workflows/docker-publish.yml/badge.svg?branch=release%2Foffline-image)](https://github.com/Parsa2820/docker-azure-agent-dind/actions/workflows/docker-publish.yml)

> This image is same as `parsa2820/docker-agent-dind`. The only difference is that the Azure agent executable file is downloaded at docker build time according to `AGENT_VERSION` build argument. The defualt behaviour of the `parsa2820/docker-agent-dind` is to ask Azure server its supported agent version and download it to container.

## Intro
The [official Microsoft documentation](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/docker?view=azure-devops#use-docker-within-a-docker-container) recommends 
to use bind mount in order to run docker inside the agent. Considering security implications of mounting Docker socket, I have installed a complete Docker inside the agent 
image itself.

## Usage
```bash
docker run -e AZP_URL=<Azure DevOps instance> -e AZP_TOKEN=<PAT token> -e AZP_AGENT_NAME=<agnet name> -e AZP_POOL=<pool name> parsa2820/azure-agent-dind-offline:latest
```

## Build
```bash
docker build --build-args AGENT_VERSION=<agent version> .
