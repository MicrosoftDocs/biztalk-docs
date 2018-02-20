---
title: "Communication Between TPs (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 168dc57e-d179-4fda-9a5b-c4da9ba26799
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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
  
-   [Fundamental Terms for TPs and LUs](../core/fundamental-terms-for-tps-and-lus-cpi-c-2.md)  
  
-   [Sample TPs Illustrating Fundamental Concepts](../core/sample-tps-illustrating-fundamental-concepts-cpi-c-2.md)  
  
-   [Configuring and Controlling TPs](../core/configuring-and-controlling-tps-cpi-c-2.md)  
  
-   [Creating TPs and Their Supporting Configuration](../core/creating-tps-and-their-supporting-configuration-cpi-c-2.md)