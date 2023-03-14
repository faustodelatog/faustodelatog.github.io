---
layout: post_img
author: fausto
image: /assets/images/conways_law.jpeg
title: Conway’s Law in Software Architecture
categories: tecnologia
excerpt: Organizations which design systems … are constrained to produce designs which are copies of the communication structures of these organizations..
---

In 1967 M. Conway enunciated a phrase at the end of his publication [*How do committees invent?*](http://www.melconway.com/Home/Committees_Paper.html) This phrase was made popular by [*Fred Brooks*](https://en.wikipedia.org/wiki/Fred_Brooks) on his book [The Mythical Man-Month.](htthttps://en.wikipedia.org/wiki/The_Mythical_Man-Monthp://) with the name of **Conway’s Law.**

<br/>
<span style="color: grey;"> *“… organizations which design systems … are constrained to produce designs which are copies of the communication structures of these organizations.” M. Conway – 1967.*</span>
<br/>
<br/>

Although this is not a scientific law, it is a valid proposition for many environments, and we can perceive it in our workplace or in other companies that develop software.
<br/>
<br/>

The organizational structure of a company will reflect in the systems produced by this organization; if there is an invoicing department, there will be an invoicing system for sure, if there is a notifications area, a system called NOTSYS (with such a cool name) will exist, the finance department will have a FINSYS, and so on, and the systems will integrate with each other in the same way the organization departments communicate.<br/>
<br/>

This law also plays a role at the construction time of every of these systems, because the **architecture of these products will reflect the communication structure of the teams that are part of that process**<br/>
<br/>

Due to this fact, if the technology department is organized around technical capabilities, with a work group focused on the user interface, other group to the database, other to the infrastructure, other to the process management, another to the implementation of business logic on the server side (figure 1) the architecture of the resulting systems (figure 2) will be very similar to these communication structures.
<br/>
<br/>
![Technical organization of teams](/assets/images/conwaylaw_1.jpg)<br/>
<br/>
*figure 1 – Technical organization of teams*<br/><br/>

![Architecture driven by technical capabilities](/assets/images/conwaylaw_2.jpg)<br/>
<br/>
*figure 2 – Architecture driven by technical capabilities*<br/><br/>

Systems are dynamic, there will always be changes, and these are often caused by changes to the business definitions; if an organizational structure is driven by technical capabilities, every change in the business definitions will require work from all the technical areas of the organization, budget and time assignment, etc. This is one of the reasons why some organizations try to group requirements to “optimize” time and resources, lengthening the development process until all the necessary work can be “justified”, which leads to the business insatisfaction towards the technology department.
<br/>
<br/>
In the other hand, we can find organizations that favour multidisciplinary or cross-functional teams formed by different roles and guided by the business capabilities (figure 3) where changes produced by new business definitions are executed from begin to end by just one team avoiding processes overhead, producing different, and often more distributed, architectures (figure 4) with greater evolution capacity.<br/>
<br/>

![Organization of teams driven by business capabilities](/assets/images/conwaylaw_3.jpg)<br/>
<br/>
*figure 3 – Organization of teams driven by business capabilities*<br/><br/>

![Business Driven Architecture](/assets/images/conwaylaw_4.jpg)<br/>
<br/>
*figure 4 – Business Driven Architecture*<br/><br/>

In the end, software is the product of an intellectual and collaborative process that will reflect the ideas of the people involved in this process and the communication structures between teams, as we have seen. Due to this, we should take in account this law at the time when we are structuring teams depending on what we want to achieve.<br/>
<br/>

Translated from the original in Spanish. 
*Thanks for the translation Carlos Oquendo* <@andres19_05>
