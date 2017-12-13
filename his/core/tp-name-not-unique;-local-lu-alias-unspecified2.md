---
title: "TP Name Not Unique; Local LU Alias Unspecified2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ee1a60e-3972-4fb1-a136-8aef23e525f0
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TP Name Not Unique; Local LU Alias Unspecified
If it does not matter on which system an invokable TP runs, use the same name for multiple invokable TPs, but do not specify an LU alias in the registry or environment variables for the TPs. In such a situation, there are no associated aliases in the list of available invokable TP names on a Host Integration Server computer. Thus, a request received from an invoking TP cannot cause a mismatch on the LU alias, and will match according to the TP name.  
  
 If you set the **DloadMatchLocalFirst** registry entry to **NO**, as described in the *Microsoft Host Integration Server Reference*, the server randomly routes the request to one of the available TPs. This spreads the processing load among multiple systems, and provides hot backup (so that you can take systems online and offline without disrupting service).  
  
## See Also  
 [Transaction Programs](../core/transaction-programs2.md)   
 [TP Name Unique for Each TP (Transaction Programs)](../core/tp-name-unique-for-each-tp-transaction-programs-1.md)   
 [TP Name Not Unique; Local LU Alias Unique](../core/tp-name-not-unique;-local-lu-alias-unique2.md)   
 [Invoking Transaction Programs](../core/invoking-transaction-programs1.md)   
 [Invoking TPs and Host Integration Server Configuration](../core/invoking-tps-and-host-integration-server-configuration1.md)   
 [Invokable Transaction Programs](../core/invokable-transaction-programs2.md)   
 [Invokable TPs and the Host Integration Server Configuration](../core/invokable-tps-and-the-host-integration-server-configuration1.md)