---
description: "Learn more about: Entity Framework"
title: "Entity Framework2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Entity Framework
The Entity Framework is a set of technologies in ADO.NET that facilitate the development of data-oriented applications. Architects and developers of data-oriented applications need to achieve two very different objectives. They must model the entities, relationships, and logic of the business problems, and they must also work with the underlying data storage engines. Data may also span multiple storage systems, each with its own protocols. For applications that work with a single storage system, the requirements of the storage system must be balanced against the requirements of writing efficient and maintainable application code.

 The Entity Framework solves these problems by enabling you to work at a higher level of abstraction with data in the form of domain-specific objects and properties, such as customers and customer addresses. Its application-centric conceptual model includes types with inheritance, complex members, and relationships, freeing you from hard-coded dependencies to a particular data engine or storage schema. You can change the mappings between the conceptual model and the storage schema without modifying your application code. Language-Integrated Query (LINQ) provides compile-time syntax validation for queries against a conceptual model. The Entity Framework significantly decreases the amount of application code that you need to write by eliminating the tightly-coupled dependency on underlying data structures. For more information, see [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/) (https://go.microsoft.com/fwlink/?LinkId=199019).

 The Host Integration Server (HIS) Entity Provider for DB2 works with the Entity Framework to allow enterprise developers to integrate existing information stored in IBM DB2 databases with new data-aware applications based on entities and data models. The topics in this section provide walkthroughs that demonstrate how to use this functionality in your applications.

 The Entity Provider for DB2 supports the Entity Data Model Tools in Visual Studio, which allow you to create an .edmx file from a database or a graphical model and then update that file when either the database or model changes. When generating an entity model using these tools, you must specify a value for the Default Qualifier connection property of the underlying MsDb2Client ADO.NET Framework Provider for DB2, which allows the provider to fetch the correct scope of DB2 catalog (tables, views, stored, procedures, columns and parameters) based on the target DB2 schema (collection).

## In This Section
 [Dynamic Data Web](../core/dynamic-data-web1.md)

 [WCF Data Service](../core/wcf-data-service1.md)

## See Also
 [Data Integration (Configuration)](../core/data-integration-configuration-2.md)