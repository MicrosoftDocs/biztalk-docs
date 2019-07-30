---
title: "Execute Commands in a DB2 Database | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c1a9736-7a3a-41fd-8fa1-e27420fa4497
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Execute Commands in a DB2 Database
The `Microsoft.HostIntegration.MsDb2Client.MsDb2Command` object exposes several `Execute` methods that you can use to perform the intended action. When you are returning results as a stream of data, use `Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteReader%2A` to return a `DataReader` object. Use `Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteScalar%2A` to return a singleton value. Use `Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteNonQuery%2A` to execute commands that do not return rows.  
  
## Use MsDb2Command with Stored Procedures  
 When you use the `Microsoft.HostIntegration.MsDb2Client.MsDb2Command` object with a stored procedure, you can set the `CommandType` property of the `MsDb2Command` object to `StoredProcedure`. With a `CommandType` of `StoredProcedure`, you can use the `Parameters` property of the `Command` to access input and output parameters and return values. The `Parameters` property can be accessed regardless of the `Execute` method called. However, when you call `Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteReader%2A`, return values and output parameters cannot be accessed until the `DataReader` is closed.  
  
 Note that SQL statements that modify data (such as `INSERT`, `UPDATE`, or `DELETE`) do not return rows. Similarly, many stored procedures perform an action but do not return rows. To execute commands that do not return rows, create an `MsDb2Command` object with the appropriate SQL command and an `Microsoft.HostIntegration.MsDb2Client.MsDb2Connection`, including any required `Microsoft.HostIntegration.MsDb2Client.MsDb2Parameters`. Execute the command by using the `ExecuteNonQuery` method of the `Microsoft.HostIntegration.MsDb2Client.MsDb2Command` object. The `Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteNonQuery%2A` method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed. If multiple statements are executed, the value returned is the sum of the records affected by all the statements executed.  
  
## Modify Databases and Catalogs  
 To execute a command to modify a database or catalog, such as the `CREATE TABLE` or `CREATE PROCEDURE` statement, create an `Microsoft.HostIntegration.MsDb2Client.MsDb2Command` object by using the appropriate SQL statements and an `Microsoft.HostIntegration.MsDb2Client.MsDb2Connection` object. Execute the command by using the `Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteNonQuery%2A` method of the `Microsoft.HostIntegration.MsDb2Client.MsDb2Command` object.  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db21.md)   
 [Managed Provider for DB2 Programmer's Guide](../core/managed-provider-for-db2-programmer-s-guide2.md)   