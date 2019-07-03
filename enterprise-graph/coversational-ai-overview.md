---
title: Using Conversational AI with Enterprise Graph by Microsoft
description: Learn how to use conversational AI with Enterprise Graph by Microsoft
author: microsteve

ms.service: enterprise-graph
ms.topic: tutorial
ms.date: 07/02/2019
ms.author: sramesh
---

# Tutorial: Create an intent classifier model

In this tutorial, you'll learn to:

> [!div class="checklist"]
> * Rank interpretations 
> * Annotate an utterance
> * Update the language models 

## Prerequisites

- Have completed all the essential steps to build the graph.

## Introduction

The Conversational AI tool, part of Microsoft Enterprise Graph lets users write natural language queries to generate SPARQL, create and annotate the language models. Annotating means that users can interpret and improve the result of a given query through continual feedback, and more on this will be covered later. This document will describe the Sasho tool’s main functions. 


The Sasho tooling is found in the Conversational AI section, pictured below: 

![Location](media/conversationalai-tooling/conversationalai-location.png)

## Language Models

Sasho assumes that you already have an ontology and data in place. Behind the scenes, Sasho builds language models on top of the ontology. Language models are a set of generated rules which Sasho uses to interpret natural language queries. Users can generate the baseline language model by clicking the Bootstrap button.

![Bootstrap](media/conversationalai-tooling/bootstrapping.png)