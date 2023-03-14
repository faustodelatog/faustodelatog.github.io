---
layout: post_img
author: fausto
title: Architecture Process – Example
image: /assets/images/architecture_example.jpg
excerpt: Join me to this great example of Architecture process
tags: tecnology
categories: tecnology
---

## The business problem

Recently I had a requirement because of a new retention policy regulation: we need to store certain files the company generate among all the business units, into one single repository, this repository is a third-party out of our control tool.<br/><br/>

Additionally we have few applications where files are generated, uploaded and saved; a couple of mechanisms are used, for instance in one application the files are saved into the database (I don´t know why but they are), in other system the files are stored in the Distributed File System, and another one uses ftp to load files.<br/><br/>

We saw a good opportunity to change the heterogeneous way to deal with files across all the applications, looking for a reusable solution based on the business capabilities related with files and document management in an homogeneous way.<br/><br/>

## Drilling down features and restrictions

After a couple of sessions with the stakeholders and the BA’s, we could determine what are the minimum features that will enable the usability of the solution, as well we defined which restrictions we should keep in mind.<br/><br/>


## Designing before coding<br/><br/>

Designing before coding? Yes, I know I say that; maybe some of my agile colleagues will fight with me just for the phrase, however I truthfully think that we must analyze the problem and of course even create diagrams to transmit the idea and represent the solution somehow before the implementation (responding to change over following a plan, is not the same as responding to change and not have a plan).<br/><br/>

### Decoupling and reusing<br/><br/>

We decided to create a new software component to encapsulate all the business logic to manage documents (see Figure 1); in this way we can implement the new requirement on top of this artifact, and other new related requirements, reducing the changes in the applications that will use it.<br/><br/>
![Figure 1](/assets/images/Theveryfirstdesign.jpg)<br/><br/>

*figure 1: The very first design* <br/><br/>

### Creating the architecture
*“A software architecture begins as the result of the collective set of design choices made by the team that created the very first version of a system”* [Beyond Software Architecture]<br/><br/>

In the same way we need a MVP, we need a MVA (Minimum Viable Architecture) to build the product.<br/><br/>

Among dev meetings and conversation with the business stakeholders, through the creation of sketches (See Figure 2) and whiteboard drawings, we ended up with an initial plan.<br/><br/>
![Figure 2](/assets/images/architecture_example.jpg)<br/><br/>

*figure 2: One of the architecture sketches* <br/><br/>

The plan was presented validating the requirements and restrictions in a high level perspective, walking through different scenarios based on BA’s experiences.<br/><br/>

We need to keep in mind that this is a plan, and plans can change, because requirements can change, technology can change, we are not Nostradamus “to know certainly the future” and assert that the proposal will cover all the requirements before implementing, however having a plan allows us to start building some components with a vision of the product.<br/><br/>

![Figure 3](/assets/images/thesolution.jpg)<br/><br/>

*figure 3: The Solution* <br/><br/>

## Explaining the architecture<br/><br/>


The solution (see Figure 3) is based on queues and asynchronous processing of document and files, it is based as well in independent deployable components. These decisions were made based on maximizing the reliability, scalability and decoupling over other requirements.<br/><br/>


One of the first things we need to understand is that we have two concepts here: Documents and Files. A Document is a concept that will contain basic business information like the business unit, type, application that generated and the file. A File is the actual binary file that will be stored in one external storage.<br/><br/>


We need to know that the only big purpose of this is creating and retrieving documents in a secure and reliable way.<br/><br/>

### Document Service <br/><br/>
It is the only entry point for the petitions of the different consumers, consumers can’t access to files nor documents without going through the services that this component expose (Security). It has its own data base to store and retrieve the information of the documents, and the only necessary information to ask for retrieving and storing files.
In order to attach files to the created document, this component will send messages to the “newDocuments” queue to be processed asynchronously for the “DocumentProcessorManager” component.
In order to retrieve files this component will use the “FileStorageService” component.<br/><br/>

### Document Processor Manager<br/><br/>

This component reads the messages delivered in the “newDocuments” queue, through the “FileCompass” determine where the file should be stored, and delegates the storing implementation to the “FileStorageManager” component. FileCompass is a lightweight component which knows, based on a set of rules (persistent rules, maybe a csv file or DB), where the file should be stored.
<br/><br/>

### File Storage Manager <br/><br/>

The responsibility of this component is communicate with the different external storage clients for retrieving and creating files, as well handling the errors when external storages won’t be available.<br/><br/>
### External Storage Clients<br/><br/>

With the “FileStorageManager”, they will conform the anti corruption layer [Domain Driven Design] to decouple the solution of the external storages.
<br/><br/>

### Error Handling queues<br/><br/>

The purpose of these components is assure the reliability of the application; these queues will handle the errors when the external storages won’t be available. When is not possible to retrieve a file, the request will be sent to “deliverFiles” queue, so when the service is available again the file will be sent through an email or other mechanism. When is not possible to store a file, the file will be saved in a local FileSystem and the request will be sent to “movingFiles” queue, so when the service is available again the processor will read the messages in the queue and will store the files where it was suppose at the beginning.<br/><br/>

Explaining the interaction between the consumers and the Document Service allows us summarize the solution from the consumers point of view, this is interesting for devs who will only use the new solution, and for the BA’s to understand the effort that will require add more consumers (Extensibility)
<br/><br/>

### Creating a Document<br/><br/>

A document will be stored synchronously and will send the message to attach the correspondent file asynchronously, this way we can guaranty that the request is saved and eventually the file will be attached. (see Figure 4)<br/><br/>

![Figure 4](/assets/images/Doccreationsequence.jpg)<br/><br/>

*figure 4: Document Creation Sequence* <br/><br/>
<br/><br/>

### Retrieving a Document
<br/><br/>

To retrieve just the information of the document without a file :

HTTP GET …/documents/7895<br/><br/>


To retrieve a File inside a document:<br/><br/>


HTTP GET …/documents/7895/file<br/><br/>

## Conclusions<br/><br/>
### Everything is a trade off<br/><br/>

We tried to generate a solution to satisfy all of required capabilities, of course that was not possible, in pos to get some capability we minimize other ones, in software, everything is a trade off. e.g. In order to assurance the reliability we need to sacrifice the efficiency or the synchronous processing. In order to decouple components we need to sacrifice the efficiency again. So we started to prioritize the required capabilities with the stakeholders really quick, doing questions like: “if you have to choose between, having a 2 seconds respond when the file is uploaded, against not be sure if the file can be uploaded because eventually some of the third party repositories won’t be available, Which one would you choose?”, we could get answers like we must to create a solution that won’t depend on the third party repositories, even if that means more time in the uploading or even if we need to change the user experience to not process files synchronously; in that sense we could identify the “must to do” requirements/capabilities.
<br/><br/>

### Benefits<br/><br/>

    - Easy to scale
    - Reliability – Error handling
    - Decoupled from third party storages
    - We have 2 (DocumentService, DocumentProcessor) deployable artifacts
        - Scale independently
        - Deploy independently
    - There is no need to deploy the consumers when a change is introduced in the document services
    - Responsibilities are segregated into different artifacts

<br/><br/>

### Pitfalls<br/><br/>

    - Change current error handling (new or unknown scenarios)
    - Current user experience will change
    - Eventual Consistency

