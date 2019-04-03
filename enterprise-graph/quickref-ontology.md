---
title: Enterprise Graph by Microsoft concepts - Ontology
description: Your graph is underpinned by an ontology in Enterprise Graph by Microsoft 
author: microsteve

ms.topic: conceptual
ms.service: enterprise-graph 
ms.date: 03/29/2019
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

For a practical guide to creating your ontology see [creating your ontology](ontology-tutorial.md).


