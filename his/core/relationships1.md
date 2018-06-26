---
title: "Relationships1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7e90b64-f3ad-4803-b073-463b807c0559
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Relationships
A configured Windows-initiated processing (WIP) environment is established by defining a set of WIP elements and then relating them in a manner that enables the client/client program, .NET Framework and the WIP Runtime to do the following:  
  
- Write a program .NET proxy (assembly).  
  
- Locate the Proxy IIS Virtual Directory.  
  
- Make a client call.  
  
- Transform the incoming parameters from .NET formats to wire format data streams.  
  
- Select the correct Transport protocols and destination for the call.  
  
- Transfer data to and from the host application  
  
- Transform the data stream to a .NET reply (parameters, return values, in the format expected, for example, `DataSets` vs. `DataTables`)  
  
- Return to the calling application.  
  
  The Object is the entity that the client “sees” as executed. Methods on the object are executed on a particular host based on any **ClientContext** overrides given or their associated remote environment (RE). There is a one-to-many relationship between an RE and an Object that allows for multiple Objects to be executed via the same Host definitions given by an RE.  
  
  The WIP Microsoft Management Console (MMC) Administrative Console enables these relationships to be established by using wizards or through manual configuration. After these relationships are established, client calls that result in host processing can be initiated.  
  
## See Also  
 [Windows-Initiated Processing Console](../core/windows-initiated-processing-console1.md)