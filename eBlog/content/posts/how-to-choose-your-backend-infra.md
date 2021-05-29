---
title: "How to Choose Your Backend Infra?"
author: esrodriguezpinzon
date: 2021-05-29T18:44:40-05:00
draft: true
---

¿Estás creando tu app pero no quieres administrar un servidor?

Eres una start-up que tiene altas demandas de tráfico por horas y andas escalando tus servidores?

O tal vez tienes un portal corporativo y necesitas la mejor seguridad para tus componentes?

Normalmente nos enfocamos en los requerimientos funcionales de nuestra aplicación, pero una vez tenemos, la lógica(backend), las funciones y los componentes listos para publicarse a los usuarios tenemos diferentes inconvenientes ajustando esta lógica a nuestras necesidades de seguridad, escalamiento o simplemente no tenemos el tiempo o el equipo para estar monitoreando y configurando los servidores que nuestra app necesita. 

¿cómo podemos romper esta inercia y ajustar esa lógica a nuestros requerimientos no funcionales?

🤔🤔🤔…

Actualmente tenemos muchos sabores de infraestructura, en general cuando hablamos de nube, podemos traducir nuestras necesidades no funcionales hacia algún concepto y/o herramienta de tipo:

IaaS: Máquinas virtuales, cuando necesitas alto control sobre tus redes, dependencias y/o sistema operativo base. (No es tan bueno escalando y se toma su tiempo configurar)

KaaS: Kubernetes como servicio, la mayoría de proveedores de nube(GKE, EKS, EKS, …) te ofrecen el despliegue de un cluster de manera sencilla, listo para poner tu lógica a operar. Este te permite gran control de redes, seguridad y escalabilidad, como desventaja tienen una configuración inicial que toma tiempo y tienes que tener un monitoreo para tus máquinas.

CaaS: Contenedor como servicio, en este caso pones tus capas funcionales en contenedores y solamente te preocupas por llevarlos a tu nube, funciona muy bien en escalabilidad y versatilidad, pierdes algo de control en cuanto a las redes.

PaaS: Plataforma como servicio, te proporciona la opción de desplegar tu código incluso sin configurar un contenedor, es una de las mejores formas de sacar tu primer MVP aunque tiene poca compatibilidad, generalmente acepta ciertos lenguajes.

FaaS: Función como servicio, es la mejor opción cuando tienes un proceso aislado y que necesita gran versatilidad por sí solo, por ejemplo un procesamiento de una imagen o el parseo de datos on-the-fly.

En este caso vamos a plasmar algunos ejemplos con Google Cloud Platform.

¿Tienes una plataforma con pocas funcionalidades como un blog o un portafolio?

Apóyate en funciones como servicio, en este caso Cloud Functions, es una solución económica, fácil de configurar y muy confiable. Si tu sitio comienza a crecer en funcionalidades(Más de 10) migra a una plataforma que te facilite la administración. Como la siguiente.

Estás iniciando, ya tienes un backend con múltiples funciones, a lo mejor un par de microservicios?

En este caso tienes dos opciones muy buenas Google App Engine(GAE) o Cloud Run, ambas plataformas te permiten desplegar tus microservicios de manera sencilla y te dan opciones de escalamiento, concurrencia, entre otros. Pero entonces, ¿cuál escojo? Si el lenguaje que usas se encuentra en los soportados por GAE:

Python 3

Java 11

Node js

PHP 5+

Ruby

Go 1.12+

Y adicionalmente no necesitas usar el filesystem(totalmente stateless), así sea de manera temporal, lo mejor es appengine. Para el resto de escenarios Cloud Run.

Tienes una plataforma con muchos microservicios, quieres full control sobre tus recursos y tener herramientas de monitoreo, testing, circuit-break y requerimientos no funcionales bastante robustos, la recomendación es Google Kubernetes Engine, ya que te da toda la versatilidad para mover, configurar tanto tus cargas como tu networking y seguridad, adicionalmente tienes la opción de instalar el cluster con Istio service mesh “out-of-the-box” lo cual te ahorra un buen rato de instalación del mismo.

Por aquí les dejo un artículo escrito por el equipo de google que te ayuda a escoger con un arbol de decisiones: Artículo

Eso es todo por esta vez 🙂