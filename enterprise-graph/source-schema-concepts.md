---
title: Schema maps in Enterprise Graph by Microsoft | Microsoft Docs
description: Understanding how to map your input data with schema maps in Enterprise Graph by Microsoft
author: microsteve

ms.service: enterprise-graph
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: stflanag
---

# Source schemas

**Source schemas** are how you describe the schema of the data you want to import to the graph. Conceptually, if you wanted to import a table of data to the graph, the source schema would define the headings of the columns of data in the table.

There are five overall data steps to creating your graph:

1. Decide on what use cases you are enabling and what entities you need in your ontology to support them
1. Create your source data TSV files
1. Create source schemas to map those input files
1. Create schema maps to link the input files to your ontology
1. Run your ingestion

Then later, as we've seen, you can [conflate new data sources](conflation-model-tutorial.md) and enrich the entities you have as required.

In this article, we are going to focus on step 3, source schemas.

When you are creating a source schema, you upload a sample of your input data. For example, in this screenshot, you can see the JSON-formatted sample of the first line of the Cities input data.

![Add source schema](media/schema-maps-concepts/add-source-schema.png)

Compare that to the first three lines of the input sample, for illustration:

```
Application.Cities_17940	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Kniman", "CityID": "17940", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
Application.Cities_13428	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Goose Prairie", "CityID": "13428", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "50"}
Application.Cities_16149	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Hudson Lake", "CityID": "16149", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
```

What we're interested in during this step is not the data values themselves (for example, the city name 'Kniman', the StateProvinceID of 15), but rather the data schema headings, that is, LastEditedBy, ValidTo, CityName, CityID, and so on.

> [!TIP]
> Think carefully about what data you want to include in your graph. A knowledge graph is not a data warehouse - you should only include the data you need for the user cases you are enabling.

## A schema for every source

You need a source schema for each data source that you will be bringing into your graph.

For example, you may have one source file containing information about people, and another source containing information about products. Each of these needs to have its own source schema to describe its structure.

Here you can see five different schemas uploaded, as we covered in the quickstart:

![All schema uploaded](media/schema-maps-concepts/all-schema-uploaded.png)

In this case we have five types of source information (one each for cities, countries, state/provinces, people and customers), and thus we have five source schemas.

## Subject key and source schemas

The subject key is the unique identifier for a given entity in a given source. It is in effect saying, 'This piece of input data belongs to this pre-existing entity.'

If you need to add a new field from a data source to pre-existing entities, you can use the subject key to match the new data value to the existing entities.

For example, imagine you have a source schema that defines source inputs for entities of type ```Person```, specifically ```Name```,  , and ```ContactNumber```.

If you need to update those values, for example, if some contact numbers have changed, you can reingest the new source data using the same source schema and subject key. The fact that you used the subject key means new entities will not be created, but rather the existing entities will be updated.

We'll discuss subject keys further in the [schema mapping](schema-map-concepts.md) overview.