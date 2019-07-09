---
title: Manage synonyms in Enterprise Graph by Microsoft
description: Learn how to manage synonyms in Enterprise Graph by Microsoft
author: microsteve

ms.service: enterprise-graph
ms.topic: tutorial
ms.date: 07/08/2019
ms.author: MSFTChao
---

# Tutorial: Manage synonyms
In this example, we will create a synonym conflation model to apply to the Customer entity type.

## Prerequisite
* [create an ontology](/create-ontology.md)
* [create source schemas](/create-source-schema.md)
* [create schema maps](/schema-map-tutorial.md)
* [Ingest data to your graph](/ingest-data.md)

## Create a conflation synonym model

### Create synonym file
Same as a normal [conflation model](conflation-concepts.md), conflation synonym model is just another model that helps you conflate mutiple entities into same one. It's just that all these entities need to be conflated together are synonyms to each other. Before we start to create a synonym model in the azure portal, we need to create a tsv file we called synonym file. In this file, we need to define what are the synonyms for each entity name. For example, we all know that *New York City* is also known as *The Big Apple*. Similar to *Los Angeles*, which has another name as *City of Angels*. So, with the example above, we can create the following synonym file:


 ![Synonym Example](media/conflation-synonym/synonym_example.png)

The synonym file needs to be a tsv file which has two parts, the 1st part is the entity name, and the 2nd part is a json object which has name, alias, State, and Country. Among these 4 properties, only name and alias are required for non city entity types. And the State and Country properties are only required for city type entities.

After creating the synonym file, we're now ready to create synonym model in the azure portal.

### Generate synonym model

Navigate to the **Manage synonyms** tab of the tab list in the azure portal

 ![Synonym Example](media/conflation-synonym/tab-list.png)

Choose **+Add** at the top left, and you'll see the new creation model window:

 ![Synonym Example](media/conflation-synonym/add-synonym.png)


Choose a name and optionally add a description.

When you choose 'Create New' from the 'Create model from' option (as opposed to upload an existing conflation model), you will see additional options:


 ![Synonym Example](media/conflation-synonym/add-synonym2.png)

 When you click the Entity type, you can choose one type of the entites from the drop down list you want to conflate with. If you don't see any thing from the drop down list, there could be something wrong with your source schema. Make sure that you have your schema map created correctly. And check the box of **Merge synonym sets that overlap** if you want to. Also, if you want to do create the synonym conflation model for city type entity, please check the **Is city conflation model**. Once you checked it, you'll four more blocks are provided.

  ![Synonym Example](media/conflation-synonym/add-synonym3.png)

In the newly prompted blocks, you need to provide the entity type and ontology property for both state and country entities. Why are these required? An example will be,  if there're two city entities with name vancouver in your graph, one is Vancouver, WA, USA and another one actually represents Vancouver, BC, Canada. The system may conflate these two together as one entity if you don't provide the state and country values correctly. With the state and country values provided accurately, the conflation system will understand that these two vancouver entities are actually different entities, and will not incorrectly conflate them together.

Finally, click the **Import synonym file** to upload the synonym file we created at the beginning of this section. And click the **Add Model** button, you're successfully created a synonym model for your conflaiton system.

Once you saved your synonym model, it will show up in your **Manage synonyms** portal.

  ![Synonym Example](media/conflation-synonym/manage-synonym.png)

As the picture shows, as long as your synonym model status is **Published**, your synonym model is successfully registered with conflation system. And with next time data ingestion, the synonym conflation will work as you defined.