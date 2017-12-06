---
title: "Invokable TPs and the Host Integration Server Configuration1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4ba782b-74bd-4f57-83ed-e35a8dd12745
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Invokable TPs and the Host Integration Server Configuration
For Host Integration Server to receive requests from an invoking TP on another system, and then route those requests to an invokable TP, certain parameters must be configured correctly:  
  
-   Host Integration Server must have a connection to the system from which the invoking TP's request is sent.  
  
-   Host Integration Server must have a remote LU capable of receiving the incoming request. This remote LU can be configured either explicitly or implicitly. When configured explicitly, there is an explicit match between a remote LU alias on Host Integration Server and the alias of the LU that conveys the invoking TP's request.  
  
     When configured implicitly, an Implicit Incoming Remote LU (with its Implicit Incoming Mode) is used. Several items must work together. First, the LU alias specified in the incoming request (the LU alias requested for the invokable TP) must match a local LU alias on the server receiving the request. Second, the local LU on the server must have an Implicit Incoming Remote LU assigned to it. The properties of the Implicit Incoming Remote LU will be used for that LU-LU session. For more details about how an Implicit Incoming Remote LU works, see [Implicit Incoming Remote LU and Implicit Incoming Mode](../core/implicit-incoming-remote-lu-and-implicit-incoming-mode.md), earlier in this section.  
  
-   Appropriate local LUs must be defined in the Host Integration Server configuration file.  
  
## See Also  
 [TP Name Unique for Each TP (Transaction Programs)](../core/tp-name-unique-for-each-tp-transaction-programs.md)   
 [TP Name Not Unique; Local LU Alias Unique](../core/tp-name-not-unique;-local-lu-alias-unique.md)   
 [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified.md)   
 [Invoking Transaction Programs](../core/invoking-transaction-programs.md)   
 [Invoking TPs and Host Integration Server Configuration](../core/invoking-tps-and-host-integration-server-configuration.md)   
 [Invokable Transaction Programs](../core/invokable-transaction-programs.md)   
 [Transaction Programs](../core/transaction-programs.md)