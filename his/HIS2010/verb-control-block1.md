---
title: "Verb Control Block1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35d08d1f-ea0b-42e4-a5f0-4415f9746fe5
caps.latest.revision: 3
---
# Verb Control Block
The only parameter passed to the **APPC** function is the address of a verb control block (VCB). The VCB is a structure made up of variables that:  
  
-   Identify the APPC verb to be executed.  
  
-   Supply information to be used by the verb.  
  
-   Contain information returned by the verb when execution is complete.  
  
 Each APPC verb has its own VCB structure, which is declared in the WINAPPC.H header file. For compatibility with earlier versions, the APPC_C.H header file is also supported.  
  
 The WINAPPC.H file is supplied as part of the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] Software Development Kit (SDK).