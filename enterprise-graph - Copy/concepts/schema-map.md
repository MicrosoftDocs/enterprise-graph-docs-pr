---
title: Enterprise Graph concepts - schema maps | Microsoft Docs
description: Linking your source data to your ontology using schema maps
author: microsteve

ms.topic: conceptual
ms.service: enterprise-graph 
ms.date: 03/29/2019
ms.author: stflanag
---
# Schema map

A schema map is how you define the relationship between the data you are importing and the ontology that you have defined. This is where it sits in the graph creation process:

1. Prepare input data
1. Define ontology
1. Create source schema
1. **Create schema map**
1. Data ingestion
1. Data conflation

The purpose of a schema map is to map your input data to the entity information in your graph, i.e. to map from your source schema to your ontology. 

For example, imagine you are working to create entities representing cities. In your source data you have a column of data called 'Name'. You want that to end up being used to populate the 'CityName' attribute in your ontology. 

So what happens in each step is:

1. You create your input data TSV
1. You define your ontology. In the example files we use in this help documentation, the cities entity is ```Application.Cities```, and it has the property CityName.
1. In the source schema, you define 'Name' as one of the source data columns
1. In the schema map, you effectively enact this statement: 'The data in the 'Name' column of my input data should be used to populate the CityName property of the ```Application.Cities``` entities'
1. When you run the ingestion, the entity for each individual city (i.e. the 'rows' of your input data) is created, e.g. Paris, London, Dublin, New York, etc. In each case, the CityName property for the create entity comes from the 'Name' column in your input data.

You take the final step, conflation, when you are adding new data to the graph. If for example you wanted to update the population number for a given city, can use the SubjectKey identifier to ensure that the information of the existing entity is updated, rather than a new entity created.



