---
title: GitLab CI/CD
season: summer
tags: CI/CD Gitlab Pipeline Devops Git
toc: true
comments: true
---

GitLab CI/CD es una herramienta para el desarrollo de software utilizando las metodologías continuas. 
Use GitLab CI/CD para detectar fallas y errores al principio del ciclo de desarrollo. Asegúrese de que todo el código implementado en producción cumpla con los estándares de código que estableció para su aplicación.
GitLab CI/CD puede compilar, probar, implementar y monitorear automáticamente sus aplicaciones mediante Auto DevOps.

Con el método continuo de desarrollo de software, crea, prueba e implementa continuamente cambios de código iterativos. Este proceso iterativo ayuda a reducir la posibilidad de que desarrolle un nuevo código basado en versiones anteriores con errores o fallas. Con este método, se esfuerza por tener menos intervención humana o incluso ninguna intervención, desde el desarrollo del nuevo código hasta su implementación. Los tres enfoques principales para el método continuo son:

## Continuous Integration
-   [Continuous Integration (CI)](https://docs.gitlab.com/ee/ci/introduction/index.html#continuous-integration)
Considere una aplicación que tiene su código almacenado en un repositorio de Git en GitLab. Los desarrolladores pushean cambios de código todos los días, varias veces al día. Por cada push al repositorio, puede crear un conjunto de scripts para compilar y probar su aplicación automáticamente. Estos scripts ayudan a disminuir las posibilidades de que introduzca errores en su aplicación. Esta práctica se conoce como Integración Continua. Cada cambio enviado a una aplicación, incluso a los branches de desarrollo, se construye y prueba de forma automática y continua. Estas pruebas garantizan que los cambios superen todas las pruebas, pautas y estándares de cumplimiento de códigos que estableció para su aplicación. GitLab en sí mismo es un ejemplo de un proyecto que utiliza la integración continua como método de desarrollo de software. Por cada impulso al proyecto, se ejecuta un conjunto de comprobaciones contra el código.

## Continuous Delivery
-   [Continuous Delivery (CD)](https://docs.gitlab.com/ee/ci/introduction/index.html#continuous-delivery)
Continuous Delivery es un paso más allá de la Integración Continua. Su aplicación no solo se crea y prueba cada vez que se envía un cambio de código a la base de código, sino que la aplicación también se implementa continuamente. Sin embargo, con la entrega continua, desencadena las implementaciones manualmente. Continuous Delivery verifica el código automáticamente, pero requiere la intervención humana para activar manual y estratégicamente la implementación de los cambios.

## Continuous Deployment
-   [Continuous Deployment (CD)](https://docs.gitlab.com/ee/ci/introduction/index.html#continuous-deployment)
La implementación continua es un paso más allá de la integración continua, similar a Continuous Delivery. La diferencia es que en lugar de implementar su aplicación manualmente, la configura para que se implemente automáticamente. No se requiere intervención humana.

Este flujo de trabajo muestra los pasos principales en el proceso de GitLab. No necesita ninguna herramienta externa para entregar su software y puede visualizar todos los pasos en la interfaz de usuario de GitLab:
![GitLab workflow example](https://docs.gitlab.com/ee/ci/introduction/img/gitlab_workflow_example_11_9.png)

[[GIT]]