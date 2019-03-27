---
title: Enterprise Graph concepts - Inheritance | Microsoft Docs
description: Inheritance between entities in your ontology
author: microsteve

ms.topic: conceptual
ms.service: enterprise-graph 
ms.date: 03/29/2019
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

