---
title: "Invokable Transaction Programs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 298cdd1c-40ad-4d9f-b636-f0e73a07a5db
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Invokable Transaction Programs
An invokable TP is a TP that can be invoked by another TP. Invokable TPs are written or configured to supply their names to Host Integration Server as a notification that they are available for incoming requests. Host Integration Server invokable TPs can be run on any Host Integration Server computer or on a Windows client.  
  
 There are two types of invokable TPs:  
  
- **Operator-started invokable TPs**  
  
   An operator-started invokable TP must be started by an operator before the TP can be invoked. When the operator-started invokable TP is started, it notifies Host Integration Server of its availability by issuing a RECEIVE_ALLOCATE verb. RECEIVE_ALLOCATE provides the name of the invokable TP.  
  
- **Autostarted invokable TPs**  
  
   An autostarted invokable TP can be started by Host Integration Server when needed. The TP must be registered on its local system, so that it can be identified to Host Integration Server. (For details about how the TP is registered, see *Microsoft Host Integration Server APPC Applications* or *Microsoft Host Integration Server CPI-C Applications*.) The registered information defines the TP as autostarted, and must specify the TP name. The registered information may also specify the local LU alias that the invokable TP will use.  
  
   If no local LU alias is registered with autostarted TPs, the resulting Host Integration Server configuration can be more flexible in responding to invoking requests.  
  
   After an autostarted invokable TP is started by Host Integration Server, the TP issues RECEIVE_ALLOCATE (just as an operator-started TP does). RECEIVE_ALLOCATE must provide the same TP name as was registered for the TP.  
  
  Each Host Integration Server maintains a list of invokable TP names and any LU aliases associated with the TP names. When a request comes in from an invoking TP, Host Integration Server compares the requested invokable TP name and the associated LU alias to the list of available invokable TPs (which may include associated LU aliases). For details about how this comparison is carried out, see *Microsoft Host Integration Server APPC Applications* or *Microsoft Host Integration Server CPI-C Applications*.  
  
  If a match is found, Host Integration Server signals the system containing the requested TP to connect to that Host Integration Server computer.  
  
  If no match is found, Host Integration Server rejects the incoming request.  
  
## See Also  
 [Transaction Programs](../core/transaction-programs2.md)   
 [TP Name Unique for Each TP (Transaction Programs)](../core/tp-name-unique-for-each-tp-transaction-programs-1.md)   
 [TP Name Not Unique; Local LU Alias Unique](../core/tp-name-not-unique;-local-lu-alias-unique2.md)   
 [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified2.md)   
 [Invoking Transaction Programs](../core/invoking-transaction-programs1.md)   
 [Invoking TPs and Host Integration Server Configuration](../core/invoking-tps-and-host-integration-server-configuration1.md)   
 [Invokable TPs and the Host Integration Server Configuration](../core/invokable-tps-and-the-host-integration-server-configuration1.md)