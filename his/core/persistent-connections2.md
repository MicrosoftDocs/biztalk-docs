---
title: "Persistent Connections2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 552e8072-56cc-42d6-925d-a702a67af905
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Persistent Connections
Windows-initiated processing (WIP) supports persistent connections over TCP/IP and SNA for the following programming models:  
  
- IMS Connect  
  
- TCP Transaction Request Message (TRM) Link  
  
- TCP Enhanced Listener Message (ELM) Link  
  
- TCP Transaction Request Message (TRM) User Data  
  
- TCP Enhanced Listener Message (ELM) User Data  
  
- OS/400 DPC  
  
- CICS Link LU 6.2  
  
- CICS User Data LU 6.2  
  
  Persistent connections are not supported in the following programming models:  
  
- IMS LU 6.2  
  
  Windows-initiated processing (WIP) persistent connections allow you to maintain a single TCP connection or SNA conversation over multiple method calls to the host. In Host Integration Server 2000, COMTI had to open and close a connection each time a method call was made to the host. On the mainframe side, CICS had to start and stop a transaction program (TP). In Host Integration Server, persistent connections allow Transaction Integrator (TI) to open a connection for the first method in a group of methods, make all the method calls, and then close the connection. On the mainframe side, CICS starts an instance of the transaction program, keeps the instance active between method calls, and then stops the program after the last call.  
  
  One of the major benefits from using persistent connections is that it allows CICS to maintain state across multiple method calls and allows for the use of local variables. Persistent connections are implemented and managed through the COMTIContext.  
  
  **COMTIContext** supports methods that flow to the .NET Framework application and updates client status information (**COMTIContext** array) or closes persistent connections.  
  
  **UpdateContextInfo** updates the clients **COMTIContext** array with information obtained from the .NET Framework application object, but with no server object involvement.  
  
  **ClosePersistentConnection** closes persistent connections by contacting the .NET Framework application object, but with no server object involvement.  
  
  The client can obtain connection state information by calling the **GetConnectionInfo** method that is implemented by the **COMTIContext** object. In the case of a .NET Framework method failure, the client must call **UpdateContextInfo** before it calls **GetConnectionInfo**.  
  
  A time-out mechanism reclaims orphaned persistent connections. The new **COMTIContext** keyword **CONNTIMEOUT** takes an integer value specifying, in seconds, how much time elapses before a persistent connection is considered abandoned, and then automatically closed. The timing starts as the client call processing is completed by the .NET Framework generic object.  
  
  **GetConnectionInfo** querys the status of a persistent connection. The following shows a .NET-based method:  
  
```  
GetConnectionInfo (ref object[] contextArray,   
    out bool fConnectionIsPersistent,   
    out bool fConnectionIsViable).  
```  
  
 The **COMTIContextArray** parameter is updated to reflect the state of the connection, the **pfConnectionIsPersistent** parameter contains TRUE if the connection is persistent and active, and the **pfConnectionIsViable** parameter contains TRUE if the connection is active.  
  
 **UpdateContextInfo** updates the clients **COMTIContext** array. The following shows a .NET-based method:  
  
```  
UpdateContextInfo (ref object[] contextArray).   
```  
  
 The **COMTIContextArray** parameter is updated to reflect the state of the connection. At a later time other information kept in the .NET Framework application might also be returned in the update **COMTIContextArray**.  
  
 **ClosePersistentConnection** closes a persistent connection without the need for a call to the server system. The following shows a .NET-based method:  
  
```  
      ClosePersistentConnection (ref object[]COMTIContextArray).  
```  
  
 The **COMTIContextArray** parameter is updated to reflect the state of the connection.  
  
## In This Section  
  
-   [How To Use a Persistent Connection](../core/how-to-use-a-persistent-connection2.md)