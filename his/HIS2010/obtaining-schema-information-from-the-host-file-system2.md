---
title: "Obtaining Schema Information from the Host File System2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33bdb954-2966-4b02-8074-73fbc39c3ef6
caps.latest.revision: 3
---
# Obtaining Schema Information from the Host File System
You can obtain schema information from a database by using *schema discovery*. Schema discovery enables applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database. Different database schema elements such as tables, columns, and stored procedures are exposed through schema collections. Each schema collection contains a variety of schema information specific to the provider that is being used.  
  
 The Managed Provider for Host Files implements `HostFileConnection.GetSchema` class, and the schema information that is returned from `GetSchema` comes in the form of a `DataTable` object. `GetSchema` also provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.  
  
## In This Section  
 [Working with the Host File GetSchema Methods](../HIS2010/working-with-the-host-file-getschema-methods1.md)  
  
 [Common Schema Collections for the Host File System](../HIS2010/common-schema-collections-for-the-host-file-system2.md)  
  
## See Also  
 [Working with the Managed Data Provider For Host Files](../HIS2010/working-with-the-managed-data-provider-for-host-files2.md)   
 [BizTalk Adapter for Host Files Configuration](../HIS2010/biztalk-adapter-for-host-files-configuration2.md)