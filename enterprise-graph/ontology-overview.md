---
title: Enterprise Graph ontology overview | Microsoft Docs
description: An overview of the basic concepts involved in an ontology
author: microsteve

ms.topic: conceptual 
ms.date: 3/29/2019
ms.author: stflanag
--- 

# Ontology Overview
Creating an effective and long-lasting ontology is a very deep and broad field of study, and becoming an expert in it is well outside the scope of this documentation. However it may be useful to have an overview of the basic concepts involved in an ontology.

## Easy to understand
The framework of an ontology must be easy to understand for humans (because it needs to evolve over time and because it is intended to have a wide variety of users), and it must be quickly computable (because it is typically used to provide customized slices of data in real time). Both of these requirements mean that the ontology language must be very simple. In this section, we will cover all of the elements of the Enterprise Graph language: entities, literals, triples, properties, and types.

**Entities:** Entities are individuals, i.e. named objects in the world. Entities include particular people, specific buildings, particular countries, individuated content, e.g. films, books, and televsion shows, etc.

For example, here is a selection of the properties in the entity for Microsoft CEO Satya Nadella:

```
people.person.date_of_birth
book.author.works_written
people.person.business_employment_tenure
people.person.education
people.person.industry
people.person.profession
```

The final structure contains many more properties and reflects the use-cases that Microsoft wants to enable with this data. Also, Microsoft's ontology is designed to represent all the information in the world - defining an ontology to represent data within a specific enterprise is a simpler problem, but still complex. 

**Literals:** Literals (also known as scalars) are values of properties that are not objects. In other words, literals can be values of properties in the ontology, but they cannot themselves have values. Literals in Enterprise Graph platform include the standard data types: Uri, Text, String, Decimal, Datetime, etc.

**Properties and Types:** A type is a class or set of entities. For example, ```mso:book.author``` is a type containing all authors of publications.

A property, on the other hand, is a relation between two entities or an entity and a literal. For example, consider the following list of properties:

```
Properties from mso:book.author
book.author.active_end        datetime
book.author.active_start      datetime
book.author.coauthor          author
book.author.institution       organization
book.author.title             string
```

The elements listed in the left-hand column are properties on ```mso:book.author``` (in other words, properties whose subject is an instance of ```mso:book.author```), and the elements listed in the right-hand column are the expected types of the objects of the properties. For example, a value of the property ```mso:book.author.active_start``` (when the author started publishing) must be a date or time, and a value of ```mso:book.author.coauthor``` must be another author.

**Triples:** A triple (also known as a fact, a tuple or a relationship) is a particular instance of a property. It consists of a subject, an object, and the name/identifier of the property that relates the subject to the object. A triple simply asserts that the subject is related to the object by the given property. For example, the triple

```
<Paris, mso:location.location.contained_by, France>
```
means that Paris is contained within France, and

```
<”Tale of Two Cities”, mso:book.written_work.author, Charles Dickens>
```

means that Charles Dickens is the author of the novel “Tale of Two Cities”.

## Properties
In most cases, a property relates two entities or an entity and a literal. Some examples of properties are: ```mso:people.person.friends```, ```mso:people.person.city_of_birth```, ```mso:people.person.first_name```, etc. 

Each property has a property type, an expected type, and a cardinality.

**Property Type:** The class or set of entities that are possible subjects of the property, e.g. the type of ```mso:people.person.friends``` is ```mso:people.person```. In other words, every thing that has a friend must be a person.

**Expected Type:** The class of entities that are possible objects of the property, e.g. the expected type of ```mso:people.person.city_of_birth``` is ```mso:location.city```. In other words, everything that is someone’s city of birth must be a city. For another example, the expected type of ```people.person.date_of_birth``` is ```type.datetime```. 

**Cardinality:** Every property is either single-valued (there is only value associated with each subject of the property) or multi-valued (there can be more than one value associated with a subject of the property). An example of a single-valued property is ```people.person.date_of_birth```, and an example of a multi-valued property is ```people.person.language```. By default, a property is multi-valued.

 

## Types
A type is a set or class of entities. Every entity is an instance of one or more types, and each of these types classifies the entity from one perspective. As we saw above, each property in the ontology is associated with two types, i.e. the property type and the expected type.

Some examples: If a particular entity is a person, it is an instance of the type ```mso:people.person```. This type includes properties for birthday (```mso:people.person.date_of_birth```), gender (```mso:people.person.gender```), phone number (```mso:people.person.phone_number```), etc. If a particular person entity happens to be an author, then the entity will be an instance of the type ```mso:book.author```, which brings with it properties like ```mso:book.author.works_edited```, ```mso:book.author.books_written```, and ```mso:book.author.institution``` (an organization associated with the author). Every entity is an instance, either directly or indirectly, of the root-level type mso:type.object. This type includes properties for name (```mso:type.object.name```), alternative names (```mso:type.object.alias```), and description (```mso:type.object.description```).

There are two kinds of types in the ontology: primary entity types and relationship/value types.

**Primary Entity Types:** The types in this category have, as their instances, named things in the world. In other words, they represent natural kinds. They cover physical objects in the world, e.g. books, films, automobiles, people, etc., and they also cover named “abstract” objects, e.g. companies, songs, diseases, fields of study, news topics, etc.

**Relationship/Value Types:** These types are very different from primary entity types. Although they are classes or sets of entities, just like primary entity types, their instances are only “dummy entities”. They do not correspond to real, named objects in the world;instead they serve only to relate more than two primary entities and/or literals.

It is important to note that the distinction between primary entity types and relationship types is exhaustive and exclusive. Every type is either a primary entity type or a relationship type, and no type is both of these.

**Placeholder types:** Aside from primary entity types and relationship/value types, it is important to distinguish placeholder types. These are types in the Microsoft ontology that have no properties associated with them. For example, the type ```mso:architecture.tower``` is a placeholder type, because it exists simply to label entities as "towers". Generally speaking, placeholder types serve an indexing function; they make the structure of types easier to understand.

## Namespaces and Domains
Namespaces and Domains are two other crucial ontology concepts. Both of these things are essentially containers of types and properties, but they are used for different purposes.

**Domains:** Domains are subject-based containers of related types and properties. In other words, they serve an indexing function by bucketing types and properties that are related to the same topic. Some sample domains from the Microsoft ontology:

```
mso:astronomy
mso:boats
mso:book
mso:commerce
mso:computer
mso:conferences
```

**Namespaces:** Namespaces are also containers of types and properties, but their purpose is to eliminate naming conflicts and, more importantly, convey the authoritativeness of a type or property.