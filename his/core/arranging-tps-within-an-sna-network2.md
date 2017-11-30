---
title: "Arranging TPs Within an SNA Network2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3269be0f-1ae6-4c4e-9cd0-8d47a07ccda2
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Arranging TPs Within an SNA Network
If your installation of Microsoft® Host Integration Server contains multiple systems (multiple clients and/or multiple computers running Host Integration Server), you can place a given invokable transaction program (TP) on more than one system. When an invoking request is received in such an installation, there can be a choice of systems on which to run the invokable TP.  
  
 You can maintain specific control over this choice or you can allow Host Integration Server to make the choice randomly to distribute the load. To do this, follow the instructions in [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified-sna-2.md).  
  
 You can maintain specific control over the choice of system by setting up invokable TPs with unique names, or by setting up each invokable TP to run only with a specific, unique LU alias. With this arrangement, the information provided by the invoking TP (in the **ALLOCATE** or **MC_ALLOCATE** verb) specifies the system on which the invokable TP should run.  
  
 You can allow Host Integration Server to make the system choice randomly by setting the **DloadMatchLocalFirst** registry entry to NO and using invokable TPs that leave the local logical unit (LU) alias unspecified. Then, when an incoming request is received, it is routed randomly, rather than preferentially to the local Host Integration Server; in addition, no matter what LU alias is requested for the invokable TP, there cannot be a mismatch. Host Integration Server starts one instance of the requested TP, choosing randomly among the available systems.  
  
 This section contains:  
  
-   [TP Name Unique for Each TP](../core/tp-name-unique-for-each-tp-sna-2.md)  
  
-   [TP Name Not Unique; Local LU Alias Unique](../core/tp-name-not-unique;-local-lu-alias-unique-sna-2.md)  
  
-   [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified-sna-2.md)