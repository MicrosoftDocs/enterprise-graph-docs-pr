---
title: Enterprise Graph concepts | Microsoft Docs
description: Understanding source schemas
services: enterprise-graph
documentationcenter: enterprise-graph-docs
author: microsteve
manager: microsteve
editor: ''

ms.service: enterprise-graph
ms.devlang: NA
ms.topic: overview
ms.date: 03/14/2019
ms.author: stflanag
---

# Source schema

Your source schema is how you describe your source data. The easiest way to think of it is to picture your source data as a table. The schema map is where you define what the headings of the columns are. Eventually, entities in the graph will be created based on the data contained in the rows.

For example, consider this row from the sample data used in tutorials of this documentation (lined in the table of contents):

```
Application.Cities_17940	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Kniman", "CityID": "17940", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
```

What we're saying here is that the 'column headings' of our data are:

```
LastEditedBy
ValidTo
CityName
CityID
Location
ValidFrom
LatestRecordedPopulation
StateProvinceID
```

In the next step, schema mapping, we will map this data to our ontology, i.e. we will say things like 'The CityName data in my input data is to be used to populate the Name property of the city entity in my ontology'. But in this step, we are just defining what columns the source data has.

In practice, the way we do that is through uploading (or directly copying and pasting) sample data. For more details, see the tutorial to [create a source schema tutorial](create-source-schema.md).