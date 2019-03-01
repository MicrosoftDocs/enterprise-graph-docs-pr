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

# Planning your graph project

Some up-front planning can help you develop an ontology that works for you, and figure out the right data you need to support the use-cases you want.

## (1) Decide what use-cases you want to enable

Start with the use-cases that you are trying to enable. For example, if your aim is to enable a query like ‘Show me all the people who are based in London’, you’re going to need entities for people, entities for locations, and links that enable the ‘based in’ relationship. Start by figuring out your key use-cases.

## (2) Decide on your ontology

Your ontology will be decided by the entities, attributes and links you will need to enable your use cases. Defining an ontology of any complexity will take a few iterations to get right, and we’ll discuss it in more depth in [the ontology section reference]. With the MSEKG product, you can choose to start with an ontology we provide, use one that you may previously have created for other projects, or create one from scratch.

## (3) Understand what data you need

Your graph is not a copy of all the data in your business – it includes only the data that you need to enable the use-cases you defined. You will likely need to bring in data from different sources (a two step process – schema mapping and ingestion, both of which we’ll cover in detail in [link to those sections]). For example, let’s say you want to enable the query ‘Show me products we have sold to Microsoft’ (assuming you have sold things to Microsoft in the past). The system will need to understand the products that were included in past deals with Microsoft, and also the details of those products. That information is likely to come from at least two different systems, one with details of past sales and another with details of the products currently for sale and for sale in the past.
