---
title: Enterprise Graph by Microsoft intent classifier overview
description: Key concepts in your intent classifier for Enterprise Graph by Microsoft
author: microsteve

ms.topic: conceptual
ms.service: enterprise-graph 
ms.date: 05/01/2019
ms.author: stflanag
---

# Intent classifier overview
Intent classifier allows your application to understand what a person wants in their own words. It uses machine learning to receive user input in natural language and extract meaning from it.

## Easy to understand

**Intents:** An intent represents a task or action the user wants to perform. Define a set of intents that corresponds to actions users want to take in your application. For example, a procurement application may define several intents: ```Orders```, ```Customers``` and ```Emails```

**Utterances:** Utterances are input from the user that your application needs to interpret. A variety of different example utterances for each intent is important for 'Intent classifier' to extract intents and entities.

For example, these could be utterances for ```Orders``` intent:
* "show me the orders placed by Customer Sears"
* "find me orders from customer Microsoft"
* "customer Apple's orders"

**Entities and Tags:** Entities extract data from the utterance. Entity types give you predictable extraction of data. Entities are from published ontology, whereas tags are your customization.

