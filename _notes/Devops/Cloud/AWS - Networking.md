---
title: AWS - Networking
season: summer
tags: Devops AWS Networking Cloud
toc: true
comments: true
---

# VPC (Virtual Private Cloud)
## Amazon Virtual Private Cloud (Amazon VPC) le permite lanzar recursos de AWS en una red virtual que defina. Dicha red virtual es prácticamente idéntica a las redes tradicionales que se utilizan en sus propios centros de datos, con los beneficios que supone utilizar la infraestructura escalable de AWS

### A continuación se enumeran los conceptos clave de las VPC:

-   **Virtual Private Cloud (VPC)**: una red virtual dedicada a la cuenta de AWS.
    
-   **Subred**: un intervalo de direcciones IP en la VPC.
    
-   **Tabla de enrutamiento**: un conjunto de reglas, denominadas rutas, que se utilizan para determinar dónde se dirige el tráfico de red.
    
-   **Gateway de Internet**: una gateway que asocia a la VPC para habilitar la comunicación entre los recursos de la VPC e Internet.
    
-   **Punto de enlace de la VPC**: le permite conectar de forma privada la VPC a los servicios de AWS compatibles y a servicios de punto de enlace de VPC habilitados por PrivateLink sin necesidad de una gateway de Internet, un dispositivo NAT, una conexión de VPN ni una conexión de AWS Direct Connect. Las instancias de su VPC no necesitan direcciones IP públicas para comunicarse con los recursos del servicio. El tráfico entre su VPC y el servicio no sale de la red de Amazon. Para obtener más información, consulte [Puntos de enlace de la VPC y de AWS PrivateLink](https://docs.aws.amazon.com/es_es/vpc/latest/userguide/endpoint-services-overview.html).
    
-   **Bloque de CIDR:** enrutamiento entre dominios sin clase. Metodología de asignación de direcciones de protocolo de Internet y agregación de rutas. Para obtener más información, consulte [Enrutamiento entre dominios sin clase](http://en.wikipedia.org/wiki/CIDR_notation) en Wikipedia.