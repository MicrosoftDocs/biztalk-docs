---
title: "Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21cf4875-1c04-41cf-98f5-d1307987ca55
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server
Consider a scenario where you want to create a BizTalk application that includes two polling operations. Each polling operation polls separate tables, Employee and Customer, from the same database. When you deploy such an application in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you will need to create two receive ports. The connection URI for each receive port will be:  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>  
```  
  
 Because both receive ports are receiving polling messages from the same database on the same server, the connection URI for both will be the same. However, a BizTalk application cannot have two receive ports with the same connection URI.  
  
 To enable adapter clients to have two receive ports that poll the same database (or even the same table in a database) in a BizTalk application, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] provides a connection property, **InboundID**. You can specify any value for this connection property. By adding the inbound ID, a connection URI becomes unique. For example:  
  
 The connection URI for the port receiving polling messages for the Employee table can be:  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Employee  
```  
  
 Similarly, the connection URI for the port receiving polling messages for the Customer table can be:  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Customer  
```  
  
 Because the connection URIs become unique by adding the **InboundID** property, you can now have multiple receive ports polling the same database or table in a single BizTalk application.  
  
> [!IMPORTANT]
>  You can choose to specify the **InboundID** connection property for both the **Polling** and **TypedPolling** operations.  
  
## See Also  
 [Poll SQL Server using the SQL Adapter with BizTalk Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)