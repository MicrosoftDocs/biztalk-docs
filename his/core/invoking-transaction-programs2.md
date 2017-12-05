---
title: "Invoking Transaction Programs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68422e3a-1ed9-4296-9365-02e52429199a
caps.latest.revision: 3
---
# Invoking Transaction Programs
An invoking TP initiates a conversation with other TPs. An invoking TP can be located on any system on the SNA network.  
  
 An invoking TP identifies itself by issuing a TP_STARTED verb. TP_STARTED specifies the name of the invoking TP, and may specify the LU alias that the TP uses (or may leave the LU alias blank).  
  
 Next, the invoking TP initiates the invoking process by issuing an ALLOCATE verb. In ALLOCATE, the invoking TP specifies the name of the invokable TP, and may also specify the partner LU alias (the LU alias to be used by the invokable TP).  
  
## See Also  
 [Transaction Programs](../core/transaction-programs1.md)   
 [TP Name Unique for Each TP (Transaction Programs)](../core/tp-name-unique-for-each-tp-transaction-programs-2.md)   
 [TP Name Not Unique; Local LU Alias Unique](../core/tp-name-not-unique;-local-lu-alias-unique1.md)   
 [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified1.md)   
 [Invoking TPs and Host Integration Server Configuration](../core/invoking-tps-and-host-integration-server-configuration2.md)   
 [Invokable Transaction Programs](../core/invokable-transaction-programs1.md)   
 [Invokable TPs and the Host Integration Server Configuration](../core/invokable-tps-and-the-host-integration-server-configuration2.md)