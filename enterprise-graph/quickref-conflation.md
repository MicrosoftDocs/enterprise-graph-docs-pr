---
title: Enterprise Graph by Microsoft concepts - Conflation
description: What conflation is and why you need it
author: microsteve

ms.topic: conceptual
ms.service: enterprise-graph 
ms.date: 03/29/2019
ms.author: stflanag
---

# Conflation

Conflation is the process whereby two entities which refer to the same concept are merged into one entity.

There are two places where this commonly happens.

## Ingesting new information through an existing source

When you carry out a new ingestion event, the newly-created entities are matched to existing entities through the [subject key in the schema map](/schema-map-tutorial.md).

If it's a new entity that does not match an existing subject key, then it becomes a new entity in the graph.

If it is matched to an existing entity, it is merged with that entity.

## Ingesting new information from a new data source

If you add a new data source with a new source schema and schema map, the new source may contain information about existing entities.

To match the new entities with existing entities, you use a [conflation model](create-conflation-model.md).