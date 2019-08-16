---
title: Enterprise Graph by Microsoft input data format 
description: Understanding the correct format for your input data in Enterprise Graph by Microsoft
author: microsteve

ms.service: enterprise-graph
ms.topic: conceptual
ms.date: 03/29/2019
ms.author: stflanag
---


# Input data
The payload to be ingested to the graph should be in JSON format and associated with a document identifier called 'DocumentId'.

To ingest the payload via the blob option, the input data in the blob must be correctly formatted as a TSV file:

<DocumentId1><tab><Payload of DocumentId1 in Json Format>
<DocumentId2><tab><Payload of DocumentId2 in Json Format>
<DocumentId3><tab><Payload of DocumentId3 in Json Format>

 <DocumentIdn><tab><Payload of DocumentIdn in Json Format>
     
While the document ID is unique within a data source, the same ID can exist across different data sources.
If a new payload is ingested with an existing documentId, then the content from the previous payload of that same documentId in the graph is overwritten.

> [!TIP]
> Do not ingest more data into the Enterprise Graph platform than you need to power the use-cases you are trying to enable. 

A sample input file can be found <a href="https://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.1_Ingestion_Application.Cities.tsv">here</a>. The first three lines are below:

```
Application.Cities_17940	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Kniman", "CityID": "17940", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
Application.Cities_13428	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Goose Prairie", "CityID": "13428", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "50"}
Application.Cities_16149	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Hudson Lake", "CityID": "16149", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
```

In the [Source Schema](create-source-schema.md) stage, you define the 'columns' of this data from the keys of the JSON body. From the previous example, columns include 'LastEditedBy', 'CityName', and 'CityID'. Next, in the [Schema mapping](schema-map-tutorial.md) stage, you map the columns to your [Ontology](ontology-tutorial.md). Finally in the [Ingestion](ingest-data.md) phase, you create individual entities of your data based on the input data and the mapping.

To conveniently host the data in a place accessible to the Enterprise Graph system, use <a href="https://azure.microsoft.com/en-us/services/storage/blobs/">Azure Blob storage</a>.
