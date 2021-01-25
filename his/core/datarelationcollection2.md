---
description: "Learn more about: DataRelationCollection"
title: "DataRelationCollection2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f372c3b-1ee1-4440-8876-f9860a9fd471
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# DataRelationCollection
A `DataSet` object contains relationships in its `DataRelationCollection` object. A relationship, represented by the `DataRelation` object, associates rows in one `DataTable` with rows in another `DataTable`. It is analogous to a join path that might exist between primary and foreign key columns in a relational database. A `DataRelation` identifies matching columns in two tables of a `DataSet`.  
  
 Relationships enable navigation from one table to another within a `DataSet`. The essential elements of a `DataRelation` are the name of the relationship, the name of the tables being related, and the related columns in each table. Relationships can be built with more than one column per table by specifying an array of `DataColumn` objects as the key columns. When a relationship is added to the `DataRelationCollection`, it may optionally add a `UniqueKeyConstraint` and a `ForeignKeyConstraint` to enforce integrity constraints when changes are made to related column values.  
  
## See Also  
 [ADO.NET DataSet for Host Integration Server](../core/ado-net-dataset-for-host-integration-server2.md)   
 [Managed Provider Programmer's Guide](../core/managed-provider-programmer-s-guide2.md)
