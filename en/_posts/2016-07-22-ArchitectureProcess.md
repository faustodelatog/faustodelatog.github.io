---
layout: post_image
author: fausto
title: Architecture Process – Example
image: /assets/images/architexture_example.jpg
---

The business problem

Recently I had a requirement because of a new retention policy regulation: we need to store certain files the company generate among all the business units, into one single repository, this repository is a third-party out of our control tool.

Additionally we have few applications where files are generated, uploaded and saved; a couple of mechanisms are used, for instance in one application the files are saved into the database (I don´t know why but they are), in other system the files are stored in the Distributed File System, and another one uses ftp to load files.

We saw a good opportunity to change the heterogeneous way to deal with files across all the applications, looking for a reusable solution based on the business capabilities related with files and document management in an homogeneous way.
Drilling down features and restrictions

After a couple of sessions with the stakeholders and the BA’s, we could determine what are the minimum features that will enable the usability of the solution, as well we defined which restrictions we should keep in mind.
Business requirement / Restriction
	
Required Capability
The business could change eventually the third party tool for other tool.
	
Decoupling of implementation
The third party tool is the final repository for certain documents not all of them, we have to handle diverse final repositories as DFS, DB, FTP, SharePoint, etc.
	
Decoupling of implementation
Files will be stored in one repository or other depending on certain rules like the type of document, business unit, date, etc.
	
Extensibility
We don’t have any access to configure, start or stop services in the third party tool or any other tool.
	
Decoupling of implementation
<Conformist Approach, Anticorruption layer>
Just the entitled users can access to send and retrieve documents.
	
Secure
Users should always be able to upload files no matter if is the third party tool selected or any other tool is unavailable.
	
Reliability
Rules change always, the business need a fast answers to change.
	
Agility, Extensibility, Maintainability
Something can go wrong with third party tools, we need to handle errors in a friendly way to the user.
	
Reliability
We should avoid change the user experience for loading and retrieving files.
	
Synchronous
Loading and retrieving files duration time shouldn’t increase.
	
Efficiency
Designing before coding

Designing before coding? Yes, I know I say that; maybe some of my agile colleagues will fight with me just for the phrase, however I truthfully think that we must analyze the problem and of course even create diagrams to transmit the idea and represent the solution somehow before the implementation (responding to change over following a plan, is not the same as responding to change and not have a plan).
Decoupling and reusing

We decided to create a new software component to encapsulate all the business logic to manage documents (see Figure 1); in this way we can implement the new requirement on top of this artifact, and other new related requirements, reducing the changes in the applications that will use it.