---
title: "Communication between TPs2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50223b07-fd3f-4fd7-b951-db1d321efdd0
caps.latest.revision: 3
---
# Communication between TPs
Various hardware and software elements in the SNA environment are required for two transaction programs (TPs) to communicate with each other. The following figure shows several fundamental elements.  
  
 ![](../core/media/appc2a.gif "appc2a")  
Fundamental communications elements between type 6.2 logical units  
  
 Each TP is associated with a logical unit (LU) of type 6.2. The LU allows the TP to access the network. Several TPs can be associated with the same LU.  
  
 A partner TP can invoke another TP, which, in turn, invokes another TP, and so on. In the following figure, TP A invokes TP B and TP B invokes TP C.  
  
 ![](../core/media/appc2a.gif "appc2a")  
TP A invoking TP B and TP B invoking TP C.  
  
 This section contains:  
  
-   [Fundamental Terms for TPs and LUs](../core/fundamental-terms-for-tps-and-lus.md)  
  
-   [Sample TPs Illustrating Fundamental Concepts](../core/sample-tps-illustrating-fundamental-concepts.md)  
  
-   [Configuring and Controlling TPs](../core/configuring-and-controlling-tps.md)  
  
-   [Creating TPs and Their Supporting Configuration](../core/creating-tps-and-their-supporting-configuration.md)