---
title: Schema maps in Enterprise Graph by Microsoft 
description: Understanding how to use schema maps to map your source data to your ontology with Enterprise Graph by Microsoft
author: microsteve

ms.service: enterprise-graph
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: stflanag
---

# Schema maps

Once your schema maps are in place, the next step is to map to your ontology. To do that, you use schema maps.

First, let's have a look at the interface, which makes it clear conceptually what's happening:

![Schema mapping](./media/schema_mapping/schema_mapping_ux.png)

On the left side is the ontology that you defined in step 1, representing the concepts that you care about for the use cases you want to enable. On the right is the schema map we defined in step 2, which describe how your data is structured.

Our job now is to create the links between these two things. For example, you may want to say that type.object.name in the entity type ```Application.Cities``` should be populated by 'CityName' in your source data.

In the interface, you can create this mapping by clicking on the 'CityName' on the right, and ticking the checkbox, then clicking on ```type.object.name``` in the left column.

What we are saying here conceptually is:
* We have defined an ontology, and in that ontology is an entity of the type ```Cities```. The ```Cities``` entity has a property called ```name```
* Separately, we have created source data in a TSV file, and it contains information about cities that we want to import into the graph as Cities entities. In step 2, we created a source schema that said that the names of the cities in our input data are stored in a column called 'CityName'
* Now in the current step, we're conceptually linking our ontology and our source data. We're saying, 'In the ontology, the name field for the Cities entity should be filled out using the data in the CityName column in our source data.'

## Using a mapping file

We can complete the mapping in the interface, or we can use a mapping file. The file is defined in XML, and looks like this:

```XML
<?xml version="1.0"?>
<XmlFeedMap xmlns="http://schemas.microsoft.com/bing/mapping">
  <MappingHeader minorVersion="0" majorVersion="2" mappingName="wwi_Application_Cities_Mapping">
    <Description>Mapping for wwi:Application.Cities</Description>
    <Specification>wwi_Application_Cities</Specification>
    <Parameters>
      <Parameter type="xs:string" name="externalid" />
      <Parameter type="xs:string" name="language" />
      <Parameter type="xs:string" name="payload" />
    </Parameters>
    <Contexts>
      <Context value="'wwi'" />
    </Contexts>
  </MappingHeader>
  <Map id="wwi_Application_Cities" targetClass="http://knowledge.microsoft.com/wwi/Application#Cities">
    <Rules>
      <Map property="$subjectId" value="StringConcat('wwi_Application_Cities', '-', ./CityID)" />
      <Map property="type.object.type" value="'http://knowledge.microsoft.com/wwi/Application.Cities'" namespace="http://knowledge.microsoft.com/ekg/" />
      <Map property="type.object.type" value="'http://knowledge.microsoft.com/ekg/type.object'" namespace="http://knowledge.microsoft.com/ekg/" />
	  <Map property="type.object.name" value="./CityName" namespace="http://knowledge.microsoft.com/ekg/" />
      <Map property="Application.Cities.CityID" value="./CityID" namespace="http://knowledge.microsoft.com/wwi/" />
      <Map property="Application.Cities.CityName" value="./CityName" namespace="http://knowledge.microsoft.com/wwi/" />
      <Map property="Application.Cities.StateProvinceID" value="InvokeMap('wwi_Application_StateProvinces')" namespace="http://knowledge.microsoft.com/wwi/" />
      <Map property="Application.Cities.Location" value="./Location" namespace="http://knowledge.microsoft.com/wwi/" />
      <Map property="Application.Cities.LatestRecordedPopulation" value="./LatestRecordedPopulation" namespace="http://knowledge.microsoft.com/wwi/" />
      <Map property="Application.Cities.LastEditedBy" value="./LastEditedBy" namespace="http://knowledge.microsoft.com/wwi/" />
      <Map property="Application.Cities.ValidFrom" value="./ValidFrom" namespace="http://knowledge.microsoft.com/wwi/" />
      <Map property="Application.Cities.ValidTo" value="./ValidTo" namespace="http://knowledge.microsoft.com/wwi/" />
    </Rules>
  </Map>
  <Map id="wwi_Application_StateProvinces" targetClass="http://knowledge.microsoft.com/wwi/Application#StateProvinces">
      <Rules>
         <Map property="$subjectId" value="StringConcat('wwi_Application_StateProvinces', '-', ./StateProvinceID)" />
         <Map property="type.object.type" value="'http://knowledge.microsoft.com/wwi/Application.StateProvinces'" namespace="http://knowledge.microsoft.com/ekg/" />
         <Map property="type.object.type" value="'http://knowledge.microsoft.com/ekg/type.object'" namespace="http://knowledge.microsoft.com/ekg/" />
      </Rules>
   </Map>
</XmlFeedMap>
```

You can find this file in the sample files we've provided for Enterprise Graph. To understand the file:

* knowledge.microsoft.com/wwi is how we defined the namespace URI when we defined our ontology. You may recall that the first lines of the ontology definition file we used are:
```
   {  
      "shorthand":"wwi",
      "namespaceuri":"http://knowledge.microsoft.com/wwi",
      "types":[  
```
You can use any URL you like here when you are defining your own ontology. 

Let's look at a specific entry:

```
<Map property="type.object.name" value="./CityName" namespace="http://knowledge.microsoft.com/ekg/" />
```

What we see here is format to map the CityName data from your source schema to type.object.name within the Cities entity.

```
<Map property="Application.Cities.LatestRecordedPopulation" value="./LatestRecordedPopulation" namespace="http://knowledge.microsoft.com/wwi/" /> 
```

Similarly here, we see that we want to use the value for LatestRecordedPopulation from our source map to populate the data the for property Application.Cities.LatestRecordedPopulation.

## Creating a subject key

Of critical importance here is property type.object.subject_key - in fact, you won't be able to complete the mapping step without it.

What is a subject key? It is an identifier for a given entity which is **unique across all of your data input files**. 

It's critical because we need to have a unique identifier that can be used to put together multiple sources of information about a given entity.

For example, imagine that from a data source about Population, we want to include the population numbers for the city, and from another data source about Sales Data, we want to populate information about total sales. In each case, we are talking about the same entity, and thus the subject key for each source should be the same.

Choosing a subject key may be easy - if for example you were uploading detail about people, and each person had a unique ID which was used consistently across all of your source of data, then you could use that as a subject key.

In other cases, you will need to choose a subject key and then use it consistently yourself. In the screenshot above, for example, you can see that the subject key is created by concatenation of other properties.



