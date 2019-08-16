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
The payload to be ingested to the graph should be in JSON format and associated with an identifier called 'DocumentId'.

To successfully ingest the payload with the blob option turned on, the input data in the blob must be correctly formatted as a TSV file which looks like:

<DocumentId1><tab><Payload of DocumentId1 in Json Format>
<DocumentId2><tab><Payload of DocumentId2 in Json Format>
<DocumentId3><tab><Payload of DocumentId3 in Json Format>
...............
................
 <DocumentIdn><tab><Payload of DocumentIdn in Json Format>
     
While the documentId is unique for a given data source, the same documentid can exist across data sources.
If new payload is ingested with an existing documentId, then the content of that same documentId in the graph gets overwritten with the new payload.

> [!TIP]
> Do not ingest more data into the Enterprise Graph platform than you need to power the use-cases you are trying to enable. 

A sample input file can be found <a href="https://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.1_Ingestion_Application.Cities.tsv">here</a>. These are the first three lines of that file:

```
Application.Cities_17940	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Kniman", "CityID": "17940", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
Application.Cities_13428	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Goose Prairie", "CityID": "13428", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "50"}
Application.Cities_16149	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Hudson Lake", "CityID": "16149", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
```

In the [Source Schema](create-source-schema.md) stage, you define the 'columns' of this data from the keys of the JSON body like 'LastEditedBy', 'CityName', and 'CityID'.. Next, in the [Schema mapping](schema-map-tutorial.md) stage, you map the columns to your [Ontology](ontology-tutorial.md). Finally in the [Ingestion](ingest-data.md) phase, you create individual entities of your data based on the input data and the mapping.

To host the data in a place accessible to the Enterprise Graph system you may want to use <a href="https://azure.microsoft.com/en-us/services/storage/blobs/">Azure Blob storage</a>, but you can use any storage system.
