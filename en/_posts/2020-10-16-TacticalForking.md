---
layout: post_img
author: fausto
title: Tactical Forking 
image: /assets/images/tacticalforking.jpeg
excerpt: Tactical forking like a strategy which involves creating a separate fork of the original project to develop new features or fix issues.
---
There are occasions in which multiple teams with different needs and business priorities work on the same code base, which infers communication and overhead in coordination between them at different moments of the development cycle, increasing the cycle time, time to recover from errors, etc..<br/><br/>

Due to this (and many other reasons) many teams choose to decouple themselves from the rest, taking their domain elsewhere. For this, many use techniques such as the Strangler Application, creation of an Autonomous Bubble or even seek to migrate their domain to a new application completely independent.
<br/><br/>

These approaches are effective when dealing with legacy systems or with third-party systems, however, when it comes to applications in constant evolution, these approaches require a great effort before beginning to obtain a real benefit; There are times when they are simply endless efforts.
<br/><br/>
When we think of taking off a piece of the system to another side, what comes to mind is an extraction: take off a piece from the whole (figure 1), however, another way to see it, it is to keep the piece and remove the rest (figure 2)
<br/><br/>
![Figure 1](/assets/images/tacticalforking_1.jpg)<br/><br/>
*Figure 1*<br/><br/>
![Figure 2](/assets/images/tacticalforking_2.jpg)<br/><br/>
*Figure 2*<br/><br/>

Under this line of thinking, we could duplicate the application and begin to get rid of the components that are not of our interest. In this way one of the teams can get its own version of the application and start working on it, by reducing the coordination with the other team. This approach is called Tactical Forking<br/><br/>

What is sought with this approach is to obtain the benefit from the first moment in which each team can have its own workflow and path to production without affecting another team.<br/><br/>


###How does Tactical Forking work?<br/><br/>
![Figure 3](/assets/images/tacticalforking_3.jpg)<br/><br/>

**Forking (Duplication)**<br/><br/>

It is necessary to create a copy of the system and its deployment mechanism (tests, pipelines, etc.).
<br/><br/>
**Routing**<br/><br/>

It is necessary to have a routing mechanism that allows users or consumers to access the different parts of the systems<br/><br/>

**Refactoring**<br/><br/>

This is a key point, it is necessary to constantly refactor the code of the new application eliminating unnecessary code to have a more maintainable code base.<br/><br/>

###Use cases<br/><br/>

**Microservices**<br/><br/>

When we are implementing a microservice architecture, and we start with the Monolith First approach, we can reach a state in which the component has several domains that need independence.<br/><br/>

**Multiple teams**<br/><br/>

There are occasions in which an application was developed by a team and then other teams joined the same code base to implement other modules with different business needs, reaching a state in which there is too much coordination and communication for deployment, Correction of errors and even blockades to commit in the code due to pipelines broken by other equipment.<br/><br/>

###Considerations<br/><br/>

Take into account the components that when they change require changes in both copies of the application, for example: non-modular css files that are not served in a cdn.<br/><br/>

Finish the work, I mean reach the final state otherwise you will have two or more monoliths with a lot of code that is useless and can produce unexpected errors.<br/><br/>

Mind the “Tactical” in the name (Tactical Forking), it’s the first step, not the last one.<br/><br/>
