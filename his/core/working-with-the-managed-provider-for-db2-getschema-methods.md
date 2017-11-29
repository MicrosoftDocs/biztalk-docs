---
title: "Working with the Managed Provider for DB2 GetSchema Methods1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f137ffb1-e9fa-4095-8382-3886c4de7754
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Working with the Managed Provider for DB2 GetSchema Methods
The `Connection` classes in the Managed Provider for DB2 implement a `GetSchema` method, which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the `GetSchema` method comes in the form of a `DataTable` object. The `GetSchema` method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information that is returned.  
  
## Specifying the DB2 Schema Collections  
 The first optional parameter of the `GetSchema` method is the collection name, which is specified as a string. There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections, which are specific to each provider.  
  
#### To determine the list of supported schema collections  
  
1.  Call `GetSchema` to determine a list of supported schema collections.  
  
     You can call `GetSchema` with no arguments, or with the schema collection name “MetaDataCollections. This returns a `DataTable` object with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.  
  
## Specifying the Restriction Values for a DB2 Schema Collection  
 The second optional parameter of the `GetSchema` method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the `GetSchema` method as an array of strings. The position in the array determines the values that you can pass, and this is equivalent to the restriction number.  
  
> [!NOTE]
>  The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection, or an `ArgumentException` is thrown. There can be fewer than the maximum number of restrictions. The missing restrictions are assumed to be null (unrestricted).  
  
#### To determine the list of supported restrictions  
  
1.  Call the `GetSchema` method with the name of the restrictions schema collection, which is "Restrictions".  
  
     This returns a `DataTable` object with a list of the collection names, restriction names, default restriction values, and restriction numbers.  
  
## See Also  
 [Obtaining Schema Information from the Managed Provider for DB2](../core/obtaining-schema-information-from-the-managed-provider-for-db2.md)