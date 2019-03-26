---
title: Enterprise Graph input data format | Microsoft Docs
description: Understanding the correct format for your Enterprise Graph input data
author: microsteve

ms.service: enterprise-graph
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: stflanag
---

# Input data

To be ingested into the graph, your input data must be correctly formatted as a TSV file. 

> [!TIP]
> Do not ingest more data into the Enterprise Graph platform than you need to power the use-cases you are trying to enable. 

A sample input file can be found <a href="https://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.1_Ingestion_Application.Cities.tsv">here</a>. These are the first three lines of that file:

```
Application.Cities_17940	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Kniman", "CityID": "17940", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
Application.Cities_13428	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Goose Prairie", "CityID": "13428", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "50"}
Application.Cities_16149	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Hudson Lake", "CityID": "16149", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
```

In the [Source Schema](/source-schema-tutorial.md) stage, you define the 'columns' of this data, i.e. LastEditedBy, CityName, CityID and so on. Then in the [Schema mapping](/schema-map-tutorial.md) stage, you map those columns to your [Ontology](/ontology-tutorial.md). Then finally in the [Ingestion](/ingestion-tutorial.md) phase, you create the individual entities of your data, based on your input data and your mapping.

To host the data in a place accessible to the Enterprise Graph system you may want to use <a href="https://azure.microsoft.com/en-us/services/storage/blobs/">Azure Blob storage</a>, but you can use any storage system.

