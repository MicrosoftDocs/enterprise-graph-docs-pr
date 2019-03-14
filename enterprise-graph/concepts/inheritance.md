---
title: Overview of Enterprise Graph | Microsoft Docs
description: Common use cases for Enterprise Graph
services: enterprise-graph
documentationcenter: enterprise-graph-docs
author: microsteve
manager: microsteve
editor: ''

ms.service: enterprise-graph
ms.devlang: NA
ms.topic: overview
ms.date: 03/17/2019
ms.author: stflanag
---

# Inheritance

Entities are organized into classes which inherit from the parent class.

For example, I may have an entity of the type ```Person```, with attributes like:

```
Name
Date of birth
Location
```

For a business use case, you may want to have an an ```Employee``` entity type, which extends the ```Person``` entity with additional properties:

```
Office location
Company start date
Manager
```

In this case it makes sense for the ```Employee``` entity to inherit from the ```Person``` entity. 

To see how this works in practice, check out the [Creating your ontology tutorial](creating_your_ontology.md), and for a much more broad-ranging discussion of ontology design and implementation, see [Building sustainable ontologies](ontology-best-practices.md)