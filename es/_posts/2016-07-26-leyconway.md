---
layout: post_img
author: fausto
image: /assets/images/conways_law.jpeg
title: Ley de Conway en la Arquitectura de Software
categories: tecnologia
excerpt: Las organizaciones que diseñan sistemas … están limitadas a producir diseños que son copias de las estructuras de comunicación de estas organizaciones.
---

En 1967 M. Conway enunció una frase en la conclusión de su publicación [*How do committees invent?*](http://http://www.melconway.com/Home/Committees_Paper.html) a la que [*Fred Brooks*](http://https://en.wikipedia.org/wiki/Fred_Brooks), la popularizó con el nombre de **Ley de Conway** en su libro [The Mythical Man-Month.](htthttps://en.wikipedia.org/wiki/The_Mythical_Man-Monthp://) <br/>
<br/>

*“… las organizaciones que diseñan sistemas … están limitadas a producir diseños que son copias de las estructuras de comunicación de estas organizaciones.” M. Conway – 1967*<br/>
<br/>
<br/>

El hecho es que a pesar de no ser una [*Ley científica*](http://https://es.wikipedia.org/wiki/Ley_cient%C3%ADfica), es una proposición que es válida en muchos entornos y se la puede evidenciar en nuestro lugar de trabajo o en otras empresas que producen software.<br/>
<br/>

La división organizacional de una empresa se verá reflejada en los sistemas que esta organización produce; si existe un departamento de cobranzas, de seguro existirá el sistema de cobranzas, si existe un área de notificaciones habrá un sistema llamado SISNOT (sí que somos originales para los nombres), el departamento financiero a su vez tendrá sus SISFIN, etc. y los sistemas se integrarán o se comunicarán entre ellos tal como se comunican las divisiones de la organización.<br/>
<br/>

A su vez esta ley también entra en vigor al momento de la construcción de cada uno de estos sistemas, **la arquitectura de dichos productos reflejará la estructura de comunicación de los equipos que forman parte de este proceso.**<br/>
<br/>

Es así que si el departamento de tecnología está dividido por conceptos técnicos, encontrando grupos de trabajo destinados a la interfaz de usuario, otro grupo a la base de datos, otro a la infraestructura, otro al manejo de procesos, otro a la implementación de lógica en el lado del servidor (figura 1); la arquitectura de estos sistemas (figura 2) será muy similar a estas estructuras de comunicación.<br/>
<br/>

![División Técnica de los equipos detrabajo](/assets/images/divisiontecnicaequipos.jpg)<br/>
<br/>
*figura 1 - División técnica de los equipos de trabajo*<br/><br/>

![Arquitectura guiada por aspectos técnicos](/assets/images/Arquitecturaguiadaaspectostecnicos.jpg)<br/>
<br/>
*figura 2 – Arquitectura guiada por aspectos técnicos*<br/><br/>

Los sistemas son dinámicos, siempre existen cambios y generalmente estos son ocasionados por cambios en las definiciones del negocio, si se favorece una división organizacional por capacidades técnicas, cada cambio en la definición del negocio exigirá trabajo, asignación de presupuesto, tiempo, etc. en cada una de las áreas técnicas que componen el grupo de trabajo; esta es una de las razones por las que en algunas organizaciones se tiende a agrupar requerimientos para “optimizar” el tiempo y los recursos, alargando el proceso de desarrollo hasta que “justifique” todo el trabajo que se debe llevar a cabo, lo que lleva a la insatisfacción del negocio con respecto al departamento de tecnología.<br/>
<br/>

Por otro lado podemos encontrar organizaciones que favorecen equipos multidisciplinarios o multifuncionales que son compuestos por diferentes roles y guiados por las capacidades del negocio (figura 3) donde los cambios producidos por nuevas definiciones del negocio son ejecutados de principio a fin por un solo equipo evitando la sobre gestión de estos procesos, produciendo arquitecturas diferentes (figura 4), generalmente más distribuidas y con mayor capacidad de evolución.<br/>
<br/>

![División de equipos por capacidades de negocio](/assets/images/Divisionequiposcapacidadesnegocio.jpg)<br/>
<br/>
*figura 3 – División de equipos por capacidades de negocio*<br/><br/>

![Arquitectura guiada por el negocio](/assets/images/Arquitecturaguiadanegocio.jpg)<br/>
<br/>
*figura 4 – Arquitectura guiada por el negocio*<br/><br/>

A la final el software es producto de un proceso intelectual colaborativo, por lo que reflejará las ideas de las personas que intervienen en este proceso y como hemos visto de las estructuras de comunicación entre equipos; es por ello que tomar en cuenta esta ley nos vendría bien a la hora de estructurar los equipos dependiendo de qué queremos conseguir.<br/>
<br/>

