---
title: "Working with the Host File GetSchema Methods2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c7bd95a-6d88-4f1b-bb64-c6b894527065
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Working with the Host File GetSchema Methods
The Managed Provider for Host File `HostFileConnection` class implements a `GetSchema` method, which is used to retrieve schema information about the file system that is currently connected. The schema information that is returned from the `GetSchema` method comes in the form of a `DataTable` object. The `GetSchema` method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information that is returned.  
  
### To retrieve file system schema information  
  
1.  Create a `HostFileConnection` object that represents the connection to the host file system.  
  
2.  Retrieve the schema information by calling `HostFileConnection.GetSchema`.  
  
    1.  The first optional parameter of the `GetSchema` method is the collection name, which is specified as a string. There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections, which are specific to each provider. You can call `GetSchema` either with no parameters, or else with the schema collection name "MetaDataCollections". This returns a DataTable object with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.  
  
    2.  The second optional parameter of the `GetSchema` method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the `GetSchema` method as an array of strings. The position in the array determines the values that you can pass, and this is equivalent to the restriction number.  
  
3.  If you want to put a restriction on the Tables schema collection, consider the following:  
  
    1.  Create an array of strings with four elements.  
  
    2.  Put a value in the element that matches the restriction number.  
  
         For example, to restrict the tables returned by the `GetSchema` method to only those tables that are owned by the "dbo" role, set the second element of the array to "dbo".  
  
    3.  Pass the value into your `GetSchema` call.  
  
### To determine a list of supported restrictions on a Schema  
  
1.  Call `GetSchema` with the first parameter set to "Restrictions".  
  
     This returns a DataTable object with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.  
  
## See Also  
 [Obtaining Schema Information from the Host File System](../core/obtaining-schema-information-from-the-host-file-system1.md)   
 [BizTalk Adapter for Host Files Configuration](./biztalk-adapter-for-host-files-configuration1.md)