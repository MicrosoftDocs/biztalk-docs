---
title: "Obtaining Schema Information from the Managed Provider for DB22 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f51d7d2-59bd-4e59-b8a9-d3f6c509744a
caps.latest.revision: 3
---
# Obtaining Schema Information from the Managed Provider for DB2
You can obtain schema information from a database by using *schema discovery*. Schema discovery enables applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database. Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections. Each schema collection contains a variety of schema information specific to the provider that is being used.  
  
 The Managed Provider for DB2 implements `MsDb2Connection.GetSchema`. The schema information returned from `GetSchema` comes in the form of a `DataTable` object. `GetSchema` provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.  
  
## In This Section  
 [Working with the Managed Provider for DB2 GetSchema Methods](../core/working-with-the-managed-provider-for-db2-getschema-methods.md)  
  
 [Understanding the Schema Collections for the Managed Provider for DB2](../core/understanding-the-schema-collections-for-the-managed-provider-for-db2.md)