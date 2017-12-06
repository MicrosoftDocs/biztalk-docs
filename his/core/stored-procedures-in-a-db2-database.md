---
title: "Stored Procedures in a DB2 Database1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e183aea0-2d57-4018-ab65-4fbd7c6f7f28
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Stored Procedures in a DB2 Database
Stored procedures offer many advantages in data-driven applications. By using stored procedures, you can encapsulate database operations in a single command, optimized for best performance, and enhanced with additional security. Although you can call a stored procedure by passing the stored procedure name followed by parameter arguments as an SQL statement, using the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command.Parameters%2A> collection of <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command> object enables you to more explicitly define stored procedure parameters, and also to access output parameters and return values.  
  
 To call a stored procedure, set the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command.CommandType%2A> of the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command> object to `StoredProcedure`. After the `CommandType` is set to `StoredProcedure`, you can use the `Parameters` collection to define parameters.  
  
 You can create an <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Parameter> object by using the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Parameter> constructor, or by calling the `Add` method of the `Parameters` collection of an <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command>. `MsDb2Parameters.Add` takes as input either constructor arguments or an existing <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Parameter> `object`. When setting the Value of an <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Parameter> to a null reference, use `DBNull.Value`.  
  
 For parameters other than Input parameters, you must set the `ParameterDirection` property to specify whether the parameter type is `InputOutput`, `Output`, or `ReturnValue`.  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db2.md)