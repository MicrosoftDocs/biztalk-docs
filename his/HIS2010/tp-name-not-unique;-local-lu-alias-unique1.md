---
title: "TP Name Not Unique; Local LU Alias Unique1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41602cd0-1c68-4cd0-b76b-258d39773368
caps.latest.revision: 3
---
# TP Name Not Unique; Local LU Alias Unique
Instead of using a unique transaction program (TP) name to specify the system on which the invokable TP will run, you can give the same name to multiple invokable TPs, but associate each TP with a unique local LU alias. Configure each invokable TP (through registry or environment variables) to use a unique local LU alias. Then set up the invoking TPs so that each one is routed not only to the correct TP name but also to the correct partner LU alias for the intended invokable TP.  
  
## See Also  
 [Transaction Programs](../HIS2010/transaction-programs1.md)   
 [TP Name Unique for Each TP (Transaction Programs)](../HIS2010/tp-name-unique-for-each-tp-transaction-programs-2.md)   
 [TP Name Not Unique; Local LU Alias Unspecified](../HIS2010/tp-name-not-unique;-local-lu-alias-unspecified1.md)   
 [Invoking Transaction Programs](../HIS2010/invoking-transaction-programs2.md)   
 [Invoking TPs and Host Integration Server Configuration](../HIS2010/invoking-tps-and-host-integration-server-configuration2.md)   
 [Invokable Transaction Programs](../HIS2010/invokable-transaction-programs1.md)   
 [Invokable TPs and the Host Integration Server Configuration](../HIS2010/invokable-tps-and-the-host-integration-server-configuration2.md)