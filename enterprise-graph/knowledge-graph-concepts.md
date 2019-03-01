---
title: Overview of Enterprise Graph | Microsoft Docs
description: Describes Enterprise graph overview and key concepts
services: virtual-machines-linux
documentationcenter: enterprise-graph-docs
author: stflanag
manager: stflanag
editor: ''

ms.assetid: 7965a80f-ea24-4cc2-bc43-60b574101902
ms.service: virtual-machines-linux
ms.devlang: NA
ms.topic: overview
ms.tgt_pltfrm: vm-linux
ms.workload: infrastructure
ms.date: 11/29/2017
ms.author: rclaus
ms.custom: H1Hack27Feb2017, mvc
---

# Knowledge graph concepts

NOTE: This page needs to be updated, currently describes a property graph.

There are a few key concepts we will refer to throughout this documentation. 

## Entities
Entities represent the things in your business that you care about. You could have entities that represent people, products, projects, customers, deals, contracts, inventory or anything else you need. You can define custom entities for your business, or use entities from a standard ontology, which we’ll talk about later. 

In this simple example, let’s look at two kinds of entities: ‘Person’ and ‘Location’.

## Attributes

Entities have attributes which contain some piece of information about them. In our example, we see that the ‘Person’ entity has the attributes ‘Name’ and ‘Start date’, and the ‘Location’ entity has the attributes ‘Name’ and ‘Population’.
  
## Links

Entities link to one another with links of a particular type, defined in your ontology. So in our example, if Anne Smith worked out of the company office in Seattle, we can represent the information as:

Now imagine that we want to add an additional relationship to show who is Anne’s manager in the company. Her manager is Daniella Ku, so we need another person entity and a new relationship.

## Ontology

The ‘dictionary’ of your entities, their attributes and the types of links that they can have. The ontology is like the mapping of the entities in the graph, what data they contain, and how they can link together. Entities in the ontology have organizational relationships, e.g. ‘business.employee’ to show the an employee is part of a large ‘business’ entity or concept.

To help you get started with MSEKG we provide some initial ontologies that you can use and extend.
