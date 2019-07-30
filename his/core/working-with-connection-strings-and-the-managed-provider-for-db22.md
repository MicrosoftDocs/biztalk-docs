---
title: "Working with Connection Strings and the Managed Provider for DB22 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3a066cd-17d1-4053-b87c-a08ebd94d7fb
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Working with Connection Strings and the Managed Provider for DB2
A connection string contains initialization information passed as a parameter from a data provider to a data source, which is then parsed immediately after being set. Syntax errors generate a run-time exception, but other errors can be found only after the data source has validated the information in the connection string. After the information is validated, the data source sets various connection string options that enable the connection and allow it to be opened.  
  
 The .NET Framework 2.0 provides new capabilities for working with connection strings, such as the `MsDb2ConnectionStringBuilder` class, which facilitates building valid connection strings at run time based on user input.  
  
## In This Section  
 [Building Connection Strings](../core/building-connection-strings1.md)  
  
 [Connection String Keywords](../core/connection-string-keywords2.md)  
  
 [Storing and Retrieving Connection Strings](../core/storing-and-retrieving-connection-strings1.md)