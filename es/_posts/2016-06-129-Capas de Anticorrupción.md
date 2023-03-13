---
layout: post_img
author: fausto
title: Capas de Anticorrupción
image: /assets/images/capas_anticorrupcion.jpeg
categories: tecnologia
---
Ese momento de pánico cuando se decide cambiar la aplicación X de la que depende nuestro sistema.
<br/><br/>
Cuando construimos sistemas, la mayoría de las veces, estos dependen o necesitan de aplicaciones externas o de terceros. El momento en que una de esas aplicaciones externas necesita ser cambiada o se necesita hacer una actualización es cuando los problemas no cesan.<br/><br/>
![Figure 1!](/assets/images/figure1_capas.jpg)<br/><br/>


El mayor inconveniente muchas veces, no es que la nueva aplicación o versión no tenga las mismas funcionalidades que la anterior (de hecho muchas veces tiene más), el problema radica en que nuestro sistema está invadido de dependencias de esta aplicación externa; el problema es que nuestro dominio se ha visto corrompido por un dominio externo.<br/><br/>

![Figure 2!](/assets/images/figure2_capas.jpg)<br/><br/>

Por ejemplo: Tenemos un sistema (cajas verdes) que maneja entre otras funcionalidades,  archivos y documentos, para lo cuál se ha decidido utilizar un repositorio de archivos como Alfresco (caja amarilla). Alfresco (o cualquier otra herramienta) provee librerías o API’s que son utilizadas por nuestro sistema para la integración. En este punto nuestro sistema/dominio tiene una dependencia de la herramienta externa a lo largo de varios componentes, por lo que decimos que nuestro dominio está corrompido ya que la herramienta externa (que puede ser un dominio diferente) esta “regada” por todo lado. El momento en que decidamos cambiar la herramienta Amarilla por una Roja se deberá buscar todas las dependencias en nuestro dominio y hacer el cambio hacia las nuevas dependencias.<br/><br/>

Podemos evitar este problema introduciendo una Capa de Anticorrupción (término acuñado en el libro DDD) que nos permiten aislar las dependencias externas o de terceros, sean estas herramientas, sistemas, dominios diferentes, etc.<br/><br/>
![Figure 3!](/assets/images/figure3_capas.jpg)<br/><br/>

La idea es construir una capa intermedia entre nuestro dominio y la dependencia externa, esta capa es la responsable de hacer las transformaciones en ambos sentidos, es decir; transformar los componentes de nuestro dominio en componentes que pueda entender la dependencia externa y viceversa. De esta forma logramos aislar esta dependencia en un solo punto, de tal modo que nuestro dominio (cajas verdes) esté enfocado en resolver el problema puntual para el que fue diseñado y que cualquier cambio en la dependencia externa no afecte mayormente al comportamiento de nuestro sistema.<br/><br/>
