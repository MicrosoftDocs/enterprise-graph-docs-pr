---
title: Enterprise Graph concepts | Microsoft Docs
description: Understanding your ontology
services: enterprise-graph
documentationcenter: enterprise-graph-docs
author: microsteve
manager: microsteve
editor: ''

ms.service: enterprise-graph
ms.devlang: NA
ms.topic: overview
ms.date: 03/14/2019
ms.author: stflanag
---

# Ontology

The ontology is where you define and manage your entities. For example, if you wanted to have an entity to represent the concept of a business project, you might want it to have properties like:

```
Name
Due date
Budget
Owner
Assigned staff
Location
```

You might further have a related entity for marketing projects, which contain additional properties like:

```
Product being marketed
Product family
Product cost
Sales point of contact
```

In that case, the ```Marketing Project``` entity would inherit from the ```Project``` entity, i.e. have all of its properties plus more.

For a practical guide to creating your ontology see [creating your ontology](../creating-your-ontology.md), and for a more in-depth discussion of creating and managing ontologies, see [ontology best practices](../ontology-best-practices.md)



