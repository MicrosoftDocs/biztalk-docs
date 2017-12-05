---
title: "Invokable TPs and the Host Integration Server Configuration2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7580030d-a932-4959-8dc0-b3be21a3c3cc
caps.latest.revision: 4
---
# Invokable TPs and the Host Integration Server Configuration
For Host Integration Server to receive requests from an invoking TP on another system, and then route those requests to an invokable TP, certain parameters must be configured correctly:  
  
-   Host Integration Server must have a connection to the system from which the invoking TP's request is sent.  
  
-   Host Integration Server must have a remote LU capable of receiving the incoming request. This remote LU can be configured either explicitly or implicitly. When configured explicitly, there is an explicit match between a remote LU alias on Host Integration Server and the alias of the LU that conveys the invoking TP's request.  
  
     When configured implicitly, an Implicit Incoming Remote LU (with its Implicit Incoming Mode) is used. Several items must work together. First, the LU alias specified in the incoming request (the LU alias requested for the invokable TP) must match a local LU alias on the server receiving the request. Second, the local LU on the server must have an Implicit Incoming Remote LU assigned to it. The properties of the Implicit Incoming Remote LU will be used for that LU-LU session. For more details about how an Implicit Incoming Remote LU works, see [Implicit Incoming Remote LU and Implicit Incoming Mode](../HIS2010/implicit-incoming-remote-lu-and-implicit-incoming-mode2.md), earlier in this section.  
  
-   Appropriate local LUs must be defined in the Host Integration Server configuration file.  
  
## See Also  
 [TP Name Unique for Each TP (Transaction Programs)](../HIS2010/tp-name-unique-for-each-tp-transaction-programs-2.md)   
 [TP Name Not Unique; Local LU Alias Unique](../HIS2010/tp-name-not-unique;-local-lu-alias-unique1.md)   
 [TP Name Not Unique; Local LU Alias Unspecified](../HIS2010/tp-name-not-unique;-local-lu-alias-unspecified1.md)   
 [Invoking Transaction Programs](../HIS2010/invoking-transaction-programs2.md)   
 [Invoking TPs and Host Integration Server Configuration](../HIS2010/invoking-tps-and-host-integration-server-configuration2.md)   
 [Invokable Transaction Programs](../HIS2010/invokable-transaction-programs1.md)   
 [Transaction Programs](../HIS2010/transaction-programs1.md)