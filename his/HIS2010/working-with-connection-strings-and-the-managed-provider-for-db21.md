---
title: "Working with Connection Strings and the Managed Provider for DB21 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f684ad32-1976-4388-87be-8039d0829723
caps.latest.revision: 3
---
# Working with Connection Strings and the Managed Provider for DB2
A connection string contains initialization information passed as a parameter from a data provider to a data source, which is then parsed immediately after being set. Syntax errors generate a run-time exception, but other errors can be found only after the data source has validated the information in the connection string. After the information is validated, the data source sets various connection string options that enable the connection and allow it to be opened.  
  
 The .NET Framework 2.0 provides new capabilities for working with connection strings, such as the `MsDb2ConnectionStringBuilder` class, which facilitates building valid connection strings at run time based on user input.  
  
## In This Section  
 [Building Connection Strings](../HIS2010/building-connection-strings2.md)  
  
 [Connection String Keywords](../HIS2010/connection-string-keywords1.md)  
  
 [Storing and Retrieving Connection Strings](../HIS2010/storing-and-retrieving-connection-strings2.md)