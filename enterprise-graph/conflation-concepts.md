---
title: Understanding conflation in Enterprise Graph by Microsoft
description: Understand what conflation is and why you need to use it in Enterprise Graph by Microsoft.
author: microsteve

ms.service: enterprise-graph
ms.topic: conceptual
ms.date: 03/29/2019
ms.author: stflanag
---

# Conflation

Conflation is a process for merging two entities if they refer to the same concept. If information about the same entity is being brought in by two different sources, then these two entities must be combined into one entity in the graph. For example, if one source of data includes data about customer contact information like their address, phone number and so on, and a second source brings in their past activities like support interactions, sales, refunds etc, then the conflation process is how we ensure all this data is added to the correct entity.

## Conflation cycle

As conflation is the process of merging new data with existing graph data, there must be some existing data in the graph before conflation can be carried out. The overall cycle is:

1. Create your graph through the standard process of ontology, source schemas, schema map, and ingestion from your source data.
1. Once that version of the graph is in place, you can create your **conflation model**, a set of rules that will be applied to the input data to decide how to map it to the existing data.

For example, if you're defining a model to manage a new ingestion of information about people, you might define a rule that says: 'If the first name matches and the surname matches and the email address matches an entity that is already in the graph, this new information refers to the same entity.'

1. When you run a new ingestion to add new data to the graph, it will be conflated against the existing data based on the rules you have defined in the conflation model.

## Conflation models

In the [conflation tutorial](create-conflation-model.md), we will go through the practical steps of creating and validating a conflation model. 

At a conceptual level, what is happening is:

1. In the model, you set up the rules that will match the new data you are matching to the graph to the existing data that is already in the graph.

In a simple case, you may be inputting data about projects, and from your source data (e.g. your internal project management system), each project has a ProjectID field to consistently identify it. In this case when you are defining your conflation rules, you set a rule that says: 'If a new entity has the same ProjectID as an existing entity, then these entities are in fact the same thing and can be merged.'

In real life, however, you may not have a ProjectID field to use. In that case, you need to use some other rules to decide whether entities are the same or not. You may for example set up a rule which says 'Two project entities can be merged if the project name is the same and the project owner is the same and the budget is the same.'

We'll also discuss the various conflation rules you can use in the [conflation tutorial](create-conflation-model.md).
