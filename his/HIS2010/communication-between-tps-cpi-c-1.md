---
title: "Communication Between TPs (CPI-C)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c404aefd-72b3-4542-b5f1-12126d7938b2
caps.latest.revision: 3
---
# Communication Between TPs (CPI-C)
Various hardware and software elements in the SNA environment are required for two transaction programs (TPs) to communicate with each other. The following figure illustrates several fundamental elements.  
  
 ![](../core/media/appc2a.gif "appc2a")  
Fundamental hardware and software elements in the SNA environment  
  
 Each TP is associated with a logical unit (LU) of type 6.2. The LU enables the TP to access the network. Note that several TPs can be associated with the same LU.  
  
 A partner TP can invoke another TP, which, in turn, invokes another TP, and so on. In the following figure, TP A invokes TP B, and TP B invokes TP C.  
  
 ![](../core/media/appc2b.gif "appc2b")  
Partner TP's invoking other partners  
  
 This section contains:  
  
-   [Fundamental Terms for TPs and LUs](../HIS2010/fundamental-terms-for-tps-and-lus-cpi-c-1.md)  
  
-   [Sample TPs Illustrating Fundamental Concepts](../HIS2010/sample-tps-illustrating-fundamental-concepts-cpi-c-1.md)  
  
-   [Configuring and Controlling TPs](../HIS2010/configuring-and-controlling-tps-cpi-c-1.md)  
  
-   [Creating TPs and Their Supporting Configuration](../HIS2010/creating-tps-and-their-supporting-configuration-cpi-c-1.md)