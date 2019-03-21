---
title: Enterprise Graph concepts - Input data | Microsoft Docs
description: Setting up your graph input data
author: microsteve

ms.topic: conceptual
ms.service: enterprise-graph 
ms.date: 03/29/2019
ms.author: stflanag
---

# Input data

Your graph can combine many sources of data together in one consistent set of entities. To be ingested into the graph, your intput data must be correctly formatted as a TSV file. 

A sample input file can be found <a href="https://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.1_Ingestion_Application.Cities.tsv">here</a>. These are the first three lines of that file:

```
Application.Cities_17940	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Kniman", "CityID": "17940", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
Application.Cities_13428	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Goose Prairie", "CityID": "13428", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "50"}
Application.Cities_16149	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Hudson Lake", "CityID": "16149", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
```

In the [Source Schema](../create-source-schema.md) stage, you define the 'columns' of this data, i.e. LastEditedBy, CityName, CityID and so on. Then in the [Schema mapping](../schema-mapping.md) stage, you map those columns to your [Ontology](../creating-your-ontology.md). Then finally in the [Ingestion](../ingesting-data.md) phase, you create the individual entities of your data, based on your input data and your mapping.

