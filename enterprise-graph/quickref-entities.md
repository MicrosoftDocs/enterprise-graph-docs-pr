---
title: Enterprise Graph by Microsoft concepts - Entities
description: Entities are the building blocks of your graph in Enterprise Graph by Microsoft
author: microsteve

ms.topic: conceptual
ms.service: enterprise-graph 
ms.date: 03/29/2019
ms.author: stflanag
---
# Entities

Entities are the key building blocks of the knowledge graph. At a conceptual level, an entity is a representation of something in the world, and it has a set of properties. An entity representing a person, for example, has properties like:

```
Name
Location
Profession
Hobbies
Favorite food
```

You can define any properties you want for a person entity using the Enterprise Graph ontology. And you can also define entirely new entities, or use entities from the samples we have already supplied.

In the Knowledge Graph itself, an entity links to other entities (and to literals/scalars, i.e. non-entity pieces of information like a date or a value) with a link of a particular type.

So for example, you could enable this graph structure in your ontology.

```
Person entity -> Managed by -> Person entity
```

Then if you have an entity for Jame Smith, and she manages the employee Alan Edwards, the relationship looks like this:

```
Alan Edwards -> Managed by -> Jane Smith
```

Entities are defined and organised in your ontology, where you decide what entities exist, what properties they can have, and how they can link to one another. 