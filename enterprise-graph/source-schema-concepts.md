---
title: Creating schema maps for your data | Microsoft Docs
description: Describes how to create a schema map in Enterprise Graph
documentationcenter: enterprise-graph-docs
author: stflanag
manager: stflanag
editor: ''

ms.topic: overview
ms.date: 9/3/2019
ms.author: stflanag
---

# Understanding source schemas

**Source schemas** are how you define the data you want to import to the Enterprise Graph so that we can later map it to your ontology. Conceptually, if you wanted to import a table of data to the graph, the source schema would define the headings of the columns of data in the table.

In the next step we will define how you relate the data you are importing to the ontology you created in step one, using a **schema map**. Right now, however, we're focused on defining the **source schema**.

## Availability

To get started, navigate to the 'Map source data' section of the interface.

![Map source data](media/creating-your-ontology/1_ontology_config.png)

The source schema that you need depends on the source data you use. Input to the graph is in TSV format, and for illustration let's <a href="http://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.1_Ingestion_Application.Cities.tsv"> look at the file here.</a>

Taking the first three lines of that file as a sample, we see:

```
Application.Cities_17940	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Kniman", "CityID": "17940", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
Application.Cities_13428	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Goose Prairie", "CityID": "13428", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "50"}
Application.Cities_16149	{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Hudson Lake", "CityID": "16149", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
```

In the graph creation process, you will define the equivalent file for your input data. We recommend that you host it on <a href="https://azure.microsoft.com/en-us/services/storage/blobs/">Azure Blob Store</a>, which is what we have done for the sample file. However, you can host it anywhere that you want.

To create the source schema, you upload a sample of the data from your input file. To see this in action, go to the sample Enterprise Graph files package, and look at 02_Schema_Application.Cities.json. The entire contents of that file is:

```
{"LastEditedBy": "1", "ValidTo": "null", "CityName": "Kniman", "CityID": "17940", "Location": "null", "ValidFrom": "null", "LatestRecordedPopulation": "null", "StateProvinceID": "15"}
```

You'll recognize this as the first line of the input TSV file. You can either upload the JSON file directly, or copy and paste in the sample data in the correct format, as we've done here for the Application.Sales.Customers:

![Create source schema](media/creating-your-ontology/create_source_schema.png)

In the sample files package there are five mapping files because there are five input data files we're going to use to create our graph.

For reference, here are the five input files we're using:

* <a href="https://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.1_Ingestion_Application.Cities.tsv">City data<a>
* <a href="https://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.2_Ingestion_Application.Countries.tsv">Country data<a>
* <a href="https://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.3_Ingestion_Application.StateProvinces.tsv">State/province data<a>
* <a href="https://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.4_Ingestion_Application.People.tsv">People data<a>
* <a href="https://ekgdemosamples.blob.core.windows.net/ekgdemosamples01/12.5_Ingestion_Sales.Customers.tsv">Customer data<a>

Note though that right now, we are just taking the first line of those files to use it as a sample to create the schema map.

Once you have created all of the schema maps for your input data, you'll see something like this:

![Create source schema](media/creating-your-ontology/fields_not_mapped.png)

You see the status 'No fields mapped' in the right-hand column because while you have created your input data files and created a schema map for them, you have not yet related the data to the ontology you created in step one. We'll look at that in the next tutorial, <a href="mapping_source_data">Mapping Source Data</a>.












