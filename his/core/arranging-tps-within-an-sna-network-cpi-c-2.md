---
title: "Arranging TPs Within an SNA Network (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 132f77b0-dcb6-4338-b17e-192b03ad660c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Arranging TPs Within an SNA Network (CPI-C)
If your Host Integration Server installation contains multiple systems (clients or SNA services), you can place a given invokable transaction program (TP) on more than one system. When an invoking request is received in such an installation, there can be a choice of systems on which to run the invokable TP. You can maintain specific control over this choice. Alternatively, by following the instructions in [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified-cpi-c-2.md), you can enable SNA service to make the choice randomly to distribute the load.  
  
 You can maintain specific control over this choice of system by setting up invokable TPs with unique names, or by setting up each invokable TP to run only with a specific, unique logical unit (LU) alias. With this arrangement, the information provided by the invoking TP (in the symbolic destination name) specifies the system on which the invokable TP should run.  
  
 You can allow the SNA service to make the system choice randomly by setting the **DloadMatchLocalFirst** registry entry to NO and using invokable TPs that leave the local LU alias unspecified. Then, when an incoming request is received, it is routed randomly, rather than preferentially to the local server. In addition, no matter what LU alias is requested for the invokable TP, there cannot be a mismatch. SNA service starts one instance of the requested TP, choosing randomly among the available systems.  
  
 The following topics describe some of the possible arrangements that can be made for running TPs.  
  
 This section contains:  
  
-   [TP Name Unique for Each TP](../core/tp-name-unique-for-each-tp-cpi-c-2.md)  
  
-   [TP Name Not Unique; Local LU Alias Unique](../core/tp-name-not-unique;-local-lu-alias-unique-cpi-c-2.md)  
  
-   [TP Name Not Unique; Local LU Alias Unspecified](../core/tp-name-not-unique;-local-lu-alias-unspecified-cpi-c-2.md)