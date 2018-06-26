---
title: "Connect to a DB2 Connection Pool | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4ebe610-51ad-41c7-b740-43d06a0f12df
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Connect to a DB2 Connection Pool

## Overview
Another way to connect to a DB2 database is through a *connection pool*. Although implemented differently on the server, a connection pool is identical to a traditional connection from the perspective of a client application.  
  
 A connection pool is a set of one or more connections that the server keeps open to service requests from one or more clients. When the client is finished with a connection, the server does not terminate the connection. Instead, the connection is released back into the pool, and can then service another client. Connection pooling is frequently used in situations where clients connect, query, and terminate a connection to the server multiple times over the course of a session, such as a database server that is accessed through the Internet.  
  
## Connect and disconnect to a DB2 connection pool Using Host Integration Server  
  
1. Connect to the DB2 server with MsDb2Connection, with the `Microsoft.HostIntegration.MsDb2Client.MsDb2Connection.ConnectionPooling%2A?displayProperty=fullName` set to `true`.  
  
2. Perform your queries as you would with a traditional DB2 connection.  
  
3. Use `MsDb2Connection.Close` or `MsDb2Connection.Dispose` to end your session.  
  
   > [!NOTE]
   >  Calling `Close` or `Dispose` on a connection from a connection pool does not actually close or dispose the connection. Instead, the server returns the connection to the pool.  
  
   The following code example shows how to connect to a DB2 database using a connection pool.  
  
```  
int GetNumberOfOrders()  
{  
    MsDb2Connection conn = new MsDb2Connection(@"File Name=C:\MyConn.UDL");  
    sDb2Command cmd;  
    int numOrders = 0;  
    conn.ConnectionPooling = true;  
    conn.Open();  
    cmd = new MsDb2Command("select count(*) from orders", conn);  
    numOrders = (int)cmd.ExecuteScalar();  
    conn.Close();  
    return numOrders;  
}  
```  
  
## See Also  
 [Working with the Managed Provider for DB2](../core/working-with-the-managed-provider-for-db21.md)   
 [Connecting to and Disconnecting from a DB2 Database](../core/connecting-to-and-disconnecting-from-a-db2-database1.md)