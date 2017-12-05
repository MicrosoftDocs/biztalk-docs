---
title: "Entity Framework1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a803c61-5000-4391-96d6-227fee67f9fb
caps.latest.revision: 2
---
# Entity Framework
The Entity Framework is a set of technologies in ADO.NET that facilitate the development of data-oriented applications. Architects and developers of data-oriented applications need to achieve two very different objectives. They must model the entities, relationships, and logic of the business problems, and they must also work with the underlying data storage engines. Data may also span multiple storage systems, each with its own protocols. For applications that work with a single storage system, the requirements of the storage system must be balanced against the requirements of writing efficient and maintainable application code.  
  
 The Entity Framework solves these problems by enabling you to work at a higher level of abstraction with data in the form of domain-specific objects and properties, such as customers and customer addresses. Its application-centric conceptual model includes types with inheritance, complex members, and relationships, freeing you from hard-coded dependencies to a particular data engine or storage schema. You can change the mappings between the conceptual model and the storage schema without modifying your application code. Language-Integrated Query (LINQ) provides compile-time syntax validation for queries against a conceptual model. The Entity Framework significantly decreases the amount of application code that you need to write by eliminating the tightly-coupled dependency on underlying data structures. For more information, see [ADO.NET Entity Framework](http://go.microsoft.com/fwlink/?LinkId=199019) (http://go.microsoft.com/fwlink/?LinkId=199019).  
  
 The Host Integration Server (HIS) Entity Provider for DB2 works with the Entity Framework to allow enterprise developers to integrate existing information stored in IBM DB2 databases with new data-aware applications based on entities and data models. The topics in this section provide walkthroughs that demonstrate how to use this functionality in your applications.  
  
## In This Section  
 [Dynamic Data Web](../core/dynamic-data-web2.md)  
  
 [WCF Data Service](../core/wcf-data-service2.md)  
  
## See Also  
 [Data Integration (Configuration)](../core/data-integration-configuration-1.md)