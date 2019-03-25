---
title: Understanding conflation in Enterprise Graph by Microsoft
description: Understand what conflation is and why you need to use it
author: microsteve

ms.service: enterprise-graph
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: stflanag
---

# Conflating data

Conflation is the process of ensuring that new information is added to the graph correctly. A new piece of information may be an update to an existing entity (e.g. if a person has moved location from one city to another) or it may relate to a new entity that should be created.

In the input data, a key concept is the **Subject Key**. That is what tells the system whether the information should be added to an existing entity or whether it belongs to a new entity. We'll discuss this further below.

## Conflation cycle

Conflation is the process of adding new data to the graph correctly, so there must be some existing data in the graph before conflation can be carried out. The overall cycle is:

(1) Create your graph through the standard process of defining your ontology, creating your source schemas, defining your schema map, and completing ingestion from your source data.

(2) Once that iteration of the graph is in place, you can create your **schema model**. The model is essentially a set of rules which will be applied to the input data to decide how to map it to the existing data.

For example, if you are defining a model to manage a new ingestion of information about people, you might define a rule that says: 'If the first name matches and the surname matches and the email address matches an entity that is already in the graph, this new informatio refers to the same entity.'

(3) When you run a new ingestion to add new data to the graph, it will be conflated against the existing data based on the rules you have defined in the conflation model.

## Subject key

Understanding the role of the Subject Key is critical to conflating your graph correctly. 

In the simplest case, imagine that in your company data you have an EmployeeID which is used to refer to a specific person, i.e. every employee has an EmployeeID which is used consistently, and no two employees have the same EmployeeID. 

Then when you need to ingest new data, you can have a conflation rule which says: 'When the EmployeeID in the input data is the same as an EmployeeID in the graph, this refers to the same entity.' 

However, in many cases you will not have a consistent piece of information to use to identify a given entity, i.e. there will not be an equivalent of the EmployeeID. 

Imagine, for example, that you are ingesting information about business projects to populate ```Projects``` entities which have properties like ```Name```, ![Choose source schema](media/conflation-example/choose-source-schema.png)Owner```, ```Assigned People```, ```Summary```, ```Budget```, ```Resources``` and so on. In the event that there is no consistent 'ProjectID' or equivalent, it will be necessary to define some rules for how the system can know whether a given piece of update data relates to a new project entity it hasn't seen before, or an existing project entity. 

A simple place to start might be with the project name. If it's called the 'Seattle Network Expansion Project', for example, you can set a rule that says that if the name matches, then the update is referring to an existing entity. 

However in real life, people will refer to the project in many different ways: 'The Seattle Network Expansion Project', 'The Seattle Project', 'Seattle Network Project', and so on ad infinitum. Furthermore, at large data scales even well-thought-out rule groups will result in a set of possible answers, which need to be ranked. For more details, see this article on conflation rule types and ranking. 

The key point for our current purposes is that when there is no obvious ```SubjectKey``` candidate, you need to define one based on your knowledge of the underlying data and the powerful conflation rules available.

QUESTION FROM STEPHEN: IS THIS DONE IN CONFLATION OR SCHEMA MAPPING STAGE? OR BOTH? WHEN IS THE SUBJECT KEY MAPPED TO THE FINAL GRAPH ENTITY ID?

 # Next steps

