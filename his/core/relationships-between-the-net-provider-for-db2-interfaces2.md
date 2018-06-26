---
title: "Relationships between the .NET Provider for DB2 Interfaces2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8cf03a4-345d-4370-9e5e-4ee1fa967632
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Relationships between the .NET Provider for DB2 Interfaces
The Managed Provider for DB2 interfaces interact in different ways—with the exception of MsDb2DataAdapter, the remaining classes adhere to a rigid parent/child relationship:  
  
- An MsDb2Connection can have one MsDb2Transaction running, although it can have multiple MsDb2Commands.  
  
- An MsDb2Transaction can have one or more MsDb2Commands running.  
  
- An MsDb2Command owns one MsDb2ParameterCollection, which stores multiple MsDb2Parameters.  
  
   An MsDb2Command can also create a single MsDb2DataReader for parsing one or more resultsets.  
  
  The MsDb2DataAdapter takes advantage of all the other Managed Provider interfaces. The MsDb2DataAdapter serves as the gateway between a host DB2 system and a client-side ADO.NET DataSet. The DataSet is an important piece of the .NET data framework because it provides a mechanism for caching data in a managed environment and inferring XML schema information, basically providing a gateway between DB2 data and Microsoft Web services.  
  
## See Also  
 [Examining the Core Interface for a Managed Provider](../core/examining-the-core-interface-for-a-managed-provider1.md)   
 [Managed Provider for DB2](../core/managed-provider-for-db21.md)