---
layout: post_img
author: fausto
image: https://mono.flatheme.net/assets/images/business-simple-1-about-2.jpg
categories: tecnología
---
# **Funciones de Aptitud (Fitness Functions)**
Cuando creamos una arquitectura, lo hacemos con un propósito, y muchas (o todas) las veces pensamos que la arquitectura que estamos ideando antes de iniciar el desarrollo es la que va a cumplir el propósito, que puede ser asegurarse del rendimiento, auditabilidad, escalabilidad, mantenibilidad, etc. (los llamados requerimientos no funciones)

El hecho es que muy pocas veces (o nunca) en realidad verificamos que el propósito de la arquitectura ideada se esté cumpliendo. Así mismo cuando nos encontramos desarrollando las aplicaciones y evolucionando la arquitectura (todas las arquitecturas evolucionan), no sabemos en realidad si el desarrollo de una solución está “respetando” o preservando la arquitectura o los principios de arquitectura, y nos damos cuenta cuando ya es muy tarde.

Parte de los conceptos de una arquitectura evolutiva son las funciones de aptitud (fitness functions) que en esencia, tratan de hacer verificables las características principales de arquitectura que guían una solución de manera constante e incremental.

Es así que cuando estamos diseñando una arquitectura nos preocupamos de que la solución sea escalable o mantenible (bonitas palabras), pero que significa que sea escalable, que tenga “buen” rendimiento o que sea mantenible, justamente es aquí donde entran las fitness functions, buscando hacer más objetivas estas características mediante mecanismos de verificación constantes.

Por ejemplo: si decimos que una arquitectura busca que la solución tenga “buen” rendimiento, entonces necesitamos crear una(s) función de aptitud que defina que significa “buen rendimiento”, creando un mecanismo de control que verifique en cada nueva versión de la aplicación que las operaciones o transacciones más importantes no tomen más de medio segundo en ser ejecutadas; esta función de aptitud puede ser ejecutada en el proceso de integración o entrega continua antes de liberar un nueva versión a producción.

Si buscamos que sea mantenible y entendemos que una de los aspectos para que la solución sea mantenible es crear una arquitectura en capas dónde buscamos que solo existan dependencias en una dirección (figura 1), entonces debemos crear una función de aptitud que verifique las dependencias entre paquetes sean solamente las que hemos definido (figura 2).

![Arquitectura Capas!](/assets/images/arquitecturacapas.jpg "Figura 1")
*figura 1 –  Arquitectura en Capas*

![Función de aptitud que analiza dependencia entre capas!](/assets/images/funcionaptitud.jpg "Figura 2")
*figura 2 – Función de aptitud que analiza dependencia entre capas*

Dado que cuando estamos construyendo arquitecturas evolutivas buscamos soportar un cambio incremental y guiado a lo largo de múltiples dimensiones, es importante saber hacia donde estamos guiando el cambio y es aquí donde las funciones de aptitud juegan un papel principal, ya que son controles que nos permiten identificar si las características principales de arquitectura se están preservando al mismo tiempo que la arquitectura evoluciona, o en otras palabras: ***Las funciones de aptitud nos permiten identificar si la arquitectura está evolucionando hacia donde queremos que evolucione.***