---
title: "Running Ollama AI in Your Homelab"
date: 2024-07-11T22:26:05-04:00
toc: false
images:
tags:
  - AI
---


{{< image src="/img/ollama.png" alt="Ollama logo" position="center" 
style="border-radius: 8px;" >}}
# Ollama
 https://ollama.com/

Ollama is a platform designed to run AI models locally. It offers a streamlined experience for deploying and managing AI applications without requiring extensive cloud resources. Ollama supports a variety of models and provides tools for easy integrations and monitoring.

### Ollama installation

Starting out, we will be installing this into an Ubuntu virtual server. I am running Ubuntu server 22.04 on my local Proxmox server. once you have your base Ubuntu server ready to go, installing Ollama is super simple, we will just follow the Download instructions found on https://ollama.com/.

```shell
curl -fsSL https://ollama.com/install.sh | sh
```
Once Ollama is installed we need to pull a model to use. I am going to use llama3 for this example but you can find many more listed here https://ollama.com/library

```shell
ollama pull llama3
```
Once the model finishes pulling you can run the model with the following command.

```shell
ollama run llama3
```



### Open-webui installation

We are going to be utilizing a web interface to access our local AI instance, there is a great open source tool called /b Open-webui. /b 

```shell
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v 
open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/
open-webui:main
```




