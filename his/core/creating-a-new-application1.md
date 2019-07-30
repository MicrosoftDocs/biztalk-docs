---
title: "Creating a New Application1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d3bd540-b5f2-4000-aae1-9dc30d3a2574
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Creating a New Application
Host-initiated processing (HIP) applications represent the execution environment for Windows Server objects that are initiated or driven from host requests. The HIP application execution environment is hosted in and synonymous with a Windows service.  
  
 A HIP application can host more than one server object. A HIP application can also have more than one listening endpoint associated with it.  
  
 Application definitions are created and managed in the **Computers** node on a specific computer. When the HIP Console is first started, the **Computers** node has only a single computer defined. That single computer is the computer where the HIP administrative console is running. When the Console is first started, no applications are defined on that computer.  
  
 You can add a new application to the Transaction Integrator (TI) Manager without specifying the local environment, host environment, objects, and object views used by the application.  
  
## See Also  
 [Working with Host-Initiated Processing](../core/working-with-host-initiated-processing1.md)