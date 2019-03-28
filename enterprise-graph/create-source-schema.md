---
title: Creating source schemas for your data
description: Describes how to create a source schema in Enterprise Graph
author: microsteve

ms.service: enterprise-graph
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: stflanag
---

# Tutorial: Create a source schema

Source schemas are how you map your input data in the Enterprise Graph platform.

In this tutorial, you'll learn to:

> [!div class="checklist"]
> * Understand what data is required to define a source schema
> * How to create a source schema for your data

## Prerequisites
In this tutorial, we'll look at the same flow we covered in the quickstart but in a bit more detail.

- Have a [published ontology in place](ontology-tutorial.md)
- Understand the [key concepts of source schemas](source-schema-concepts.md)

## Prerequisites

![Source schema step](media/quickstart/12-add-source-schema.png)

1. Click on **+Add** to upload a source schema file
1. Choose an appropriate name, e.g. 'Application-People'
1. Choose the 'Upload a JSON file' option
1. Choose the 02_Schema_Application.Cities.json file to upload

You'll see the file previewed in 'Sample Data' window, and you can click OK.

Note that as covered in the [overview guide](source-schema-concepts.md), the JSON upload here just specifies the columns from your source data. We're interested in specifying the input data schema, at this point, not the input data values.

In our example, we have five types of input data - Cities, Countries, State/Provinces, People and Customers. Each one of those has a separate input file, and therefore each one needs its own schema map describing that input file. 

When all of the schema maps are created and uploaded, you see this view:

![All schemas](media/quickstart/15-all-schema-uploaded.png)

The reason we see 'No fields mapped' is because we have not defined any schema maps yet. We have created the input TSV files from your source data, and we have mapped those files in the Enterprise Graph system, but we have not yet created the link to the ontology.

Next, we'll look at schema maps to link your source data to the ontology.

> [!div class="nextstepaction"]
> [Creating schema maps](schema-map-tutorial.md)
