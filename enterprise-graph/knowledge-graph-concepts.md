---
title: Overview of Enterprise Graph | Microsoft Docs
description: Describes Enterprise graph overview and key concepts
services: virtual-machines-linux
documentationcenter: enterprise-graph-docs
author: microsteve
manager: microsteve
editor: ''

ms.assetid: 7965a80f-ea24-4cc2-bc43-60b574101902
ms.devlang: NA
ms.topic: overview
ms.date: 6/3/2019
ms.author: stflanag
---

# Knowledge graph concepts

### Triples

Triples are the building blocks of the Enterprise Graph. They are in the form Subject -> Predicate -> Object, e.g. Jane Smith -> ManagerOf -> John White. Every piece of information in the Enterprise Graph is stored this way. 

### Entities

Entities are the 'things' in your graph. For example you could have an entity of the type 'Document', and it would have properties like:

* Author
* Creation date
* Date last edited
* Collaborators
* Subject
* Related projects

With Enterprise Graph, you can define any entity and any set of properties that you want when you are creating your ontology.

The 'entity type', i.e. the 'blank entity', is defined in your ontology. Then when you actually import your data into you graph, you will have a 'filled-out' entity, e.g.:

**Document: April Status Report**
* Author: James Ryan
* Creation date: March 3, 2019
* Dates last edited: March 5, 2019
* Collaborators: Jane Williams, Aaron Skye
* Subject: Weekly status updates for the Alpha project
* Related projects: Alpha

Note one additional key concept: The value for things like 'Author', 'Collaborators' and 'Related Projects' are most likley other entites, rather than literal values. So in the graph, the entity for the document 'April Status Report' has a link of type 'Author' to the entity for the person 'James Ryan'.

### Properties

The 'attributes' of each entity are called its 'properties'. In the example above, the attributes of the entity type 'Document' are 'Author', 'Creation date', 'Date last edited' and so on. 

### Inheritance

In the Enterprise Graph system, each entity type in the ontology inherits from a 'parent type'. So for example, you may have a generic 'object' type, which in turn has a sub-class called 'vehicles', and within that you have 'cars' and 'trucks'. Within cars you have 'gas-powered' and 'electric-powered'. That's represented with dot notation, i.e.:

**object.vehicles**
**object.vehicles.trucks**
**object.vehicles.cars**
**object.vehicles.cars.gas-powered**
**object.vehicles.cars.electric-powered**

In each case, the child entity inherits properties from the parent. 

* **object.vehicles**: Has properties like length, width, price, manufacturer
* **object.vehicles.trucks**.: Has the same properties as object.vehicles but also properties like towing capacity, road clearance height
* **object.vehicles.cars**: Inherits the properties of object.vehicles but also has detail on child seat mounting points, top speed
* **object.vehicles.cars.gas-powered**: Inherits the properties of object.vehicles.cars, but also has properties for fuel economy
* **object.vehicles.cars.eletric-powered**: Inherits the properties of object.vehicles.cars, but also has properties for driving range

This is simplified example, so we can point out for example that it's not just cars that have a 'top speed' property, trucks have one also. So perhaps it would be better to put the 'top speed' property at the **object.vehicles** level. Making these kinds of decisions and figuring out the best structure for your business and use-cases is a key part of developing your ontology. 

### Links

When we say that 'an entity has a property', what we really mean is that the entity links to that piece of information. Looking again at our document from the Entities section above, and selecting some properties to focus on:

**Document: April Status Report**
* Author: James Ryan
* Creation date: March 3, 2019
* Collaborators: Jane Williams, Aaron Skye

What is happening in each case is:

* The entity for the document 'April Status Report' links to the entity for the person 'James Ryan' with the link type 'Author'
* The entity for the document 'April Status Report' links to the entity for the time/date object 
'March 3, 2019' with the link type 'Creation date'
* The entity for the document 'April Status Report' links to the entity for the person 'Jane Wiliams' with the link type 'Collaborator'
* The entity for the document 'April Status Report' links to the entity for person 'Aaoron Skye' with the link type 'Collaborator'

The power of the graph is built up through these simple links between entities, which can represent and help you understand enormously complex information.

### Ontology

The ontology is where you define your entities and their properties. Building the right ontology to represent the data you want to include and the use-cases you want to enable can be tricky, so we have provided some starter ontologies for you to use and modify.

### Conflation

When you add a new piece of information to your graph, should it be an entirely new instance of an entity (e.g. a new entity of the type 'document') or an update to an existing entity (e.g. a new property for a document that already exists in the graph)? Answering this question can be very tricky, and we have provided powerful tools to help make the right decisions.

