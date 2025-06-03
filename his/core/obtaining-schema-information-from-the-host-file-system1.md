---
description: "Learn more about: Obtaining Schema Information from the Host File System"
title: "Obtaining Schema Information from the Host File System1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Obtaining Schema Information from the Host File System
You can obtain schema information from a database by using *schema discovery*. Schema discovery enables applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database. Different database schema elements such as tables, columns, and stored procedures are exposed through schema collections. Each schema collection contains a variety of schema information specific to the provider that is being used.  
  
 The Managed Provider for Host Files implements `HostFileConnection.GetSchema` class, and the schema information that is returned from `GetSchema` comes in the form of a `DataTable` object. `GetSchema` also provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.  
  
## In This Section  
 [Working with the Host File GetSchema Methods](../core/working-with-the-host-file-getschema-methods2.md)  
  
 [Common Schema Collections for the Host File System](../core/common-schema-collections-for-the-host-file-system1.md)  
  
## See Also  
 [Working with the Managed Data Provider For Host Files](../core/working-with-the-managed-data-provider-for-host-files1.md)   
 [BizTalk Adapter for Host Files Configuration](./biztalk-adapter-for-host-files-configuration1.md)
