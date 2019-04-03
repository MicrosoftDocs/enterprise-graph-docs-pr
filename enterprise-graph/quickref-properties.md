---
title: Enterprise Graph by Microsoft concepts - Properties
description: Entities and properties in Enterprise Graph by Microsoft 
author: microsteve

ms.topic: conceptual
ms.service: enterprise-graph 
ms.date: 03/29/2019
ms.author: stflanag
---

# Properties

Properties are the attributes of an entity - an entity type ```City``` may have an attribute called ```Population``` for example.

Note that all attributes are associated with an entity by a link. So the underlying data for the above example is:

```
City -> Has a population -> Population number
```
Often, the property for a given entity is itself a property. So for example you may have the property ```Mayor``` for a city, and that property could only have the value of a ```Person``` entity (as only people can by Mayors). That relationship looks like:

```
City -> Has a mayor -> Entity of type ```Person```
```




