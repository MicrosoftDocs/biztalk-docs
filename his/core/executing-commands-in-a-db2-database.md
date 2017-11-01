---
title: "Executing Commands in a DB2 Database2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c1a9736-7a3a-41fd-8fa1-e27420fa4497
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Executing Commands in a DB2 Database
The <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command> object exposes several `Execute` methods that you can use to perform the intended action. When you are returning results as a stream of data, use <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteReader%2A> to return a `DataReader` object. Use <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteScalar%2A> to return a singleton value. Use <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteNonQuery%2A> to execute commands that do not return rows.  
  
## Using MsDb2Command with Stored Procedures  
 When you use the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command> object with a stored procedure, you can set the `CommandType` property of the `MsDb2Command` object to `StoredProcedure`. With a `CommandType` of `StoredProcedure`, you can use the `Parameters` property of the `Command` to access input and output parameters and return values. The `Parameters` property can be accessed regardless of the `Execute` method called. However, when you call <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteReader%2A>, return values and output parameters cannot be accessed until the `DataReader` is closed.  
  
 Note that SQL statements that modify data (such as `INSERT`, `UPDATE`, or `DELETE`) do not return rows. Similarly, many stored procedures perform an action but do not return rows. To execute commands that do not return rows, create an `MsDb2Command` object with the appropriate SQL command and an <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Connection>, including any required <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Parameter>`s`. Execute the command by using the `ExecuteNonQuery` method of the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command> object. The <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteNonQuery%2A> method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed. If multiple statements are executed, the value returned is the sum of the records affected by all the statements executed.  
  
## Modifying Databases and Catalogs  
 To execute a command to modify a database or catalog, such as the `CREATE TABLE` or `CREATE PROCEDURE` statement, create an <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command> object by using the appropriate SQL statements and an <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Connection> object. Execute the command by using the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command.ExecuteNonQuery%2A> method of the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Command> object.  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db2.md)   
 [Managed Provider for DB2 Programmer's Guide](../core/managed-provider-for-db2-programmer-s-guide.md)   
 [Managed Provider for DB2 Programmer's Reference &#91;bpi&#93; &#91;HIS09_R2&#93;](http://msdn.microsoft.com/en-us/a50e991f-d651-40cb-a45c-d64fa132d251)