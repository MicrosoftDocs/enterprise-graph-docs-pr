---
title: Creating your Enterprise Graph ontology | Microsoft Docs
description: Describes how to create an ontology in Enterprise Graph
documentationcenter: enterprise-graph-docs
author: stflanag
manager: stflanag
editor: ''

ms.topic: overview
ms.date: 9/3/2019
ms.author: stflanag
---

# Ontology best practices

Creating an effective and long-lasting ontology from scratch is a very deep and broad field of study, and becoming an expert in it is well outside the scope of this documentation. However, there are some general best-practices and tips we'd like to share based on our experience of building a global-level ontology to power the Bing search engine.

## Easy to understand

The framework of an ontology must be easy to understand for humans (because it needs to evolve over time and because it is intended to have a wide variety of users), and it must be quickly computable (because it is typically used to provide customized slices of data in real time). Both of these requirements mean that the ontology language must be very simple. In this section, we will cover all of the elements of the Satori Ontology language: entities, literals, triples, properties, and types.

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

**Properties and Types:** A type is a class or set of entities. For example, mso:book.author is a type containing all authors of publications.

A property, on the other hand, is a relation between two entities or an entity and a literal. For example, consider the following list of properties:

```
Properties from mso:book.author
book.author.active_end        datetime
book.author.active_start      datetime
book.author.coauthor          author
book.author.institution       organization
book.author.title             string
```

The elements listed in the left-hand column are properties on mso:book.author (in other words, properties whose subject is an instance of mso:book.author), and the elements listed in the right-hand column are the expected types of the objects of the properties. For example, a value of the property mso:book.author.active_start (when the author started publishing) must be a date or time, and a value of mso:book.author.coauthor must be another author.

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

**Property Type:** The class or set of entities that are possible subjects of the property, e.g. the type of mso:people.person.friends is mso:people.person. In other words, every thing that has a friend must be a person.

**Expected Type:** The class of entities that are possible objects of the property, e.g. the expected type of mso:people.person.city_of_birth is mso:location.city. In other words, everything that is someone’s city of birth must be a city. For another example, the expected type of people.person.date_of_birth is type.datetime. 

**Cardinality:** Every property is either single-valued (there is only value associated with each subject of the property) or multi-valued (there can be more than one value associated with a subject of the property). An example of a single-valued property is people.person.date_of_birth, and an example of a multi-valued property is people.person.language. By default, a property is multi-valued.

## Types

A type is a set or class of entities. Every entity is an instance of one or more types, and each of these types classifies the entity from one perspective. As we saw above, each property in the ontology is associated with two types, viz. the property type and the expected type.

Some examples: If a particular entity is a person, it is an instance of the type mso:people.person. This type includes properties for birthday (mso:people.person.date_of_birth), gender (mso:people.person.gender), phone number (mso:people.person.phone_number), etc. If a particular person entity happens to be an author, then the entity will be an instance of the type mso:book.author, which brings with it properties like mso:book.author.works_edited, mso:book.author.books_written, and mso:book.author.institution (an organization associated with the author). Every entity is an instance, either directly or indirectly, of the root-level type mso:type.object. This type includes properties for name (mso:type.object.name), alternative names (mso:type.object.alias), and description (mso:type.object.description).

There are two kinds of types in the ontology: primary entity types and relationship/value types.

**Primary Entity Types:** The types in this category have, as their instances, named things in the world. In other words, they represent natural kinds. They cover physical objects in the world, e.g. books, films, automobiles, people, etc., and they also cover named “abstract” objects, e.g. companies, songs, diseases, fields of study, news topics, etc.

**Relationship/Value Types:** These types are very different from primary entity types. Although they are classes or sets of entities, just like primary entity types, their instances are only “dummy entities”. They do not correspond to real, named objects in the world; instead they serve only to relate more than two primary entities and/or literals.

An example will make this clear. Consider the relationship between two people who are married. It is natural to assume that this could be represented as a property linking two people. For example, we could define a spouse property, mso:people.person.spouse, whose expected type would also be mso:people.person. With this property, one could specify that Michael is married to Stacy, for example. Now, we might also want to keep track of the date and location that a marriage began. We could add two more properties to people.person to cover this, and we could call these properties mso:people.person.wedding_date and mso:people.person.wedding_location. This scheme of representation will work, as long as we assume that both Stacy and Michael are only ever married to each other. Otherwise, we won’t know which spouse, wedding date, and wedding location correspond to which marriage.

The solution here is to create a relationship type corresponding to marriage. Each instance of this type will be a “dummy entity” whose only function is to tie together all of the information about a particular marriage. This type will include a property called mso:people.marriage.spouse to relate the people who are married to the “dummy entity” corresponding to their marriage. For example, in the case of the marriage of Stacy and Michael, each of these people is a value of the mso:people.marriage.spouse property. Furthermore, the wedding date, the wedding location, and the divorce date (if any) can be added to the marriage type as the properties mso:people.marriage.wedding_date, mso:people.marriage.wedding_location, and mso:people.marriage.divorce_date. Note that this representation can easily handle the case where Michael and/or Stacy are remarried. In this case, we simply create a new instance of the mso:people.marriage type and we use the properties on this type to assign new values to the instance.

When a relationship type is defined, it is common to add, not only properties linking “dummy entities” to the entities that participate in the relationship, but also some properties that go in the reverse direction, from the primary entities to the “dummy entities”. For example, we could add a property people.person.marriage to link each person to each marriage entity that they are or were a part of. These added properties are virtual properties whose values are populated on the basis of properties defined on the relationship type. Accordingly, these properties are not strictly necessary, because it is always possible to determine their values by means of a query or join across other properties. However, these virtual properties make it easier for users to discover relevant information. Without the people.person.marriage property, it is very difficult to know whether or not Michael is married just by looking at the Michael entity. One would have to consider every property that points to Michael, and there could easily be a very large number of such properties. Adding the people.person.marriage property creates an explicit pointer from Michael to his marriage data.

It is important to note that the distinction between primary entity types and relationship types is exhaustive and exclusive. Every type is either a primary entity type or a relationship type, and no type is both of these.

Whether a type is a primary entity type, on the one hand, or a relationship or value type, on the other, is indicated in the fourth pane when the type is selected. For example, the following information appears for the type mso:business.employment_tenure:

**Placeholder types:** Aside from primary entity types and relationship/value types, it is important to distinguish placeholder types. These are types in the ontology that have no properties associated with them. For example, the type mso:architecture.tower is a placeholder type, because it exists simply to label entities as "towers". Generally speaking, placeholder types serve an indexing function; they make the structure of types easier to understand.

## Namespaces and Domains

Namespaces and Domains are two other crucial notions in the Satori Ontology. Both of these things are essentially containers of types and properties, but they are used for different purposes.

**Domains:** Domains are subject-based containers of related types and properties. In other words, they serve an indexing function by bucketing types and properties that are related to the same topic. Some sample domains from the Microsoft ontology:

mso:astronomy
mso:boats
mso:book
mso:commerce
mso:computer
mso:conferences

Obviously there are many, many more.

**Namespaces:** Namespaces are also containers of types and properties, but their purpose is to eliminate naming conflicts and, more importantly, convey the authoritativeness of a type or property.

In Microsoft, MSO is the official namespace for the ontology used for Bing, but there are other namespaces as well, e.g. dev for development. A book in the MSO namespace is referred to mso:book, whereas in the development namespace it would be dev:book.

## Developing the Ontology

There are a number of key principles for developing an ontology without which the ontology cannot serve its essential function, i.e. a common, formal semantics for a wide variety of data sources and applications. The key themes of these principles are organization (ontology elements should be easy to find), simplicity (ontology elements should be defined in a way that factors out as much complexity as possible), and clarity (ontology elements should be named and documented so that users can easily understand their meanings).

**1. Ontology elements should be motivated by data and applications, but they should support all data and applications that are conceptually similar.** All ontology elements should have a unique, precise, application-independent meaning. 

**2. Ontology types and properties should form an inheritance structure as much as possible.** This makes it easier for users to find what they need, and it facilitates deeper and more accurate conflation. In particular, a type should be included in any type that is broader in meaning, and all properties should be assigned to the type at the appropriate level of generality. 

A property should not be assigned to a type that is too general, because then it will apply to irrelevant entities, and it should not be assigned to a type that is too specific, because then it will not apply to relevant entities. Expressing properties at the highest level of generality will not only make the ontology easier to navigate; it will eliminate much duplication of content. For example, properties that are common to sports athletes, sports teams, and sports competitions can be inherited across all of the various sports from common types.

**3. The representation in the ontology should be as simple as possible.** If a class contains entities that can be individuated and named, then it should be represented as a primary entity type. If a class does not contain entities that can be individuated and named, it should not be reified (i.e. made into a type of the ontology) unless it is needed to relate more than two entities, in which case it should be represented as a relationship type. In all other cases, it is not necessary to create a type. 

**4. Ontology elements should be named consistently and descriptively.** An example from within Microsoft: at one point location.administrative-division was divided into admin_division_1, admin_division_2, and admin_division_3. These terms might have some meaning to a specialist, but they are incomprehensible to the average user and do not allow him or her to get a footing in the classification of locations. 





