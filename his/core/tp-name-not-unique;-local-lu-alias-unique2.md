---
description: "Learn more about: TP Name Not Unique; Local LU Alias Unique"
title: "TP Name Not Unique; Local LU Alias Unique2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TP Name Not Unique; Local LU Alias Unique
Instead of using a unique transaction program (TP) name to specify the system on which the invokable TP will run, you can give the same name to multiple invokable TPs, but associate each TP with a unique local LU alias. Configure each invokable TP (through registry or environment variables) to use a unique local LU alias. Then set up the invoking TPs so that each one is routed not only to the correct TP name but also to the correct partner LU alias for the intended invokable TP.  
  
## See Also  
 [Transaction Programs](../core/transaction-programs2.md)   
 [TP Name Unique for Each TP (Transaction Programs)](../core/tp-name-unique-for-each-tp-transaction-programs-1.md)   
 [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified2.md)   
 [Invoking Transaction Programs](../core/invoking-transaction-programs1.md)   
 [Invoking TPs and Host Integration Server Configuration](../core/invoking-tps-and-host-integration-server-configuration1.md)   
 [Invokable Transaction Programs](../core/invokable-transaction-programs2.md)   
 [Invokable TPs and the Host Integration Server Configuration](../core/invokable-tps-and-the-host-integration-server-configuration1.md)
