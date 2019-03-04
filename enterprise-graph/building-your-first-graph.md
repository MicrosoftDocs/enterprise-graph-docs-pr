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

# Building your first graph

To get started with the Enterprise graph, we've provided everything you need to complete the graph-build process end to end.

## (1) Creating an ontology

Your ontology is the like the 'dictionary' of your graph, containing the definitions of the entities you want to use and what properties they have. The ontology defines the entity types, and then later we'll import data to create actual entities. So for example, in this step we'll define a 'City' entity that has a 'CityName' property, and later on we'll create actual city entites, e.g. Kniman, Cubero and so on.

To get started, choose **Configure Ontology** from the Overview page, or choose the **Configure your ontology** option from the menu blade.

 ![Creating your first ontology](media/building-your-first-graph/choose_ontology.png)

Click on the **+Add** button, and you'll see the **Add ontology version** pane.

![Add ontology pane](media/building-your-first-graph/add_ontology_pane.png)

In this pane, you can see there are options to create an ontology from scratch, modify one of the Microsoft-supplied ontologies, or import an existing ontology. For now, we're going to import a pre-created ontology, based on the <a href="http:///www.microsoft.com>World Wide Importers sample data</a>. 



# Key capabilities

* Create a graph with custom entities for your specific business, compiled from multiple data sources as required
* Resolve conflicts between different information sources to create one consistent graph of information and relationships
* Answer complex queries through the combination of data that would otherwise be in separate silos
* Bring powerful answers to all users through natural language, not just data scientists and analysts
* Discover new insights through the relationships between the entities in your graph
