---
title: Docker - Configuraciones varias
season: summer
tags: Devops, Docker, Configuraciones, Cloud, Network
toc: true
comments: true
---
# Docker - Compose 
## Network:
### HOST - Network
SI necesitamos generar un container desde compose y que la net sea el host debemos agregar, en lugar de "networkings:"
``` 
network_mode: host
```

[[Primero pasos en docker]]
#DOCKER 
#DOCKER-COMPOSE
