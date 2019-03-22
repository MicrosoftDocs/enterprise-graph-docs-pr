---
title: Deleting your ontology in Enterprise Graph by Microsoft | Microsoft Docs
description: The steps you need to take to delete your ontology Enterprise Graph by Microsoft
author: microsteve

ms.service: enterprise-graph
ms.topic: tutorial
ms.date: 03/27/2019
ms.author: stflanag
---

# Deleting your ontology

## To delete your ontology, you first need to delete your schema maps. 

> [!TIP]
> If it was possible to delete your ontology while you had source schemas which still mapped to it, the system could get into an inconsistent state. Hence the requirement to complete the steps in the first order.

## Deleting your source data maps

In the 'Map source schema' view, you can select the individual schemas you need to delete:

![Source schema view](media/deleting-ontology/source-schema-view.png)

You will need to type 'Yes' into to the text box to confirm your deletion intention.

![Source schema view](media/deleting-ontology/delete-data-source.png)

> [!CAUTION]
> You need to re-create your source schema and schema map if you need to un-do this step

Make sure that all schema maps which map to the ontology you want to delete are deleted.

## Deleting your ontology

Once the schema maps have been deleted, you can navigate to the 'Configure your ontology' section and choose 'Delete all'

![Source schema view](media/deleting-ontology/delete-ontology.png)

Again, you will need to confirm that you intend to delete all the ontologies, and not just a specific version.








