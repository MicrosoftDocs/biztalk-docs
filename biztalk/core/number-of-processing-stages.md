---
title: "Number of Processing Stages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "processing, stages"
  - "process management solution tutorial, processing stages"
ms.assetid: 74bd9f8c-99b4-4931-a096-6c54221ab2e5
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Number of Processing Stages
The solution separates the order process into stages, so that it is possible to modify the process (by replacing stages) without disrupting long-running orders. For more information about how the process was divided into stages, see "Dividing Business Processes" in [Some Design Principles in the Business Process Management Solution](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
 The current version of the solution contains only two processing stages. It could, however, contain many more. More stages provide more points where you can version the process and continue working on the latest version of a processing stage. However, each stage introduces the overhead of additional coordinating messages going through the MessageBox database, which increases processing time. You must monitor the solution's performance to determine if the number of multiple stages is excessive.  
  
## See Also  
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [Process Manager Logic](../core/process-manager-logic.md)