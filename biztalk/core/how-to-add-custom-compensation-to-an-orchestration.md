---
description: "Learn more about: How to Add Custom Compensation to an Orchestration"
title: "How to Add Custom Compensation to an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, compensations"
  - "Compensate shape [Orchestration Designer]"
  - "Compensate shape [Orchestration Designer], orchestrations"
  - "Compensation property"
  - "orchestrations, transactional"
  - "orchestrations, customizing"
  - "customizing, orchestrations"
  - "Compensate shape [Orchestration Designer], custom compensation"
ms.assetid: d153498d-8f98-42ae-90b9-e3083d669aef
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Custom Compensation to an Orchestration
An orchestration transaction that is configured as long running can have custom compensation code to reverse or undo the effects of the transaction. If the orchestration has completed successfully and has been called by another orchestration, the calling orchestration can invoke its compensation block using a **Compensate** shape.  
  
### To specify that an orchestration will use custom compensation  
  
1.  In the Orchestration View window, select **Orchestration Properties**.  
  
2.  In the Properties window, select **Custom** in the drop-down for the **Compensation** property.  
  
     The **Compensation** tab appears next to the **Orchestration** tab at the bottom of the Design Surface.  
  
### To design custom compensation for an orchestration  
  
1.  Click the **Compensation** tab at the bottom of the Design Surface.  
  
     The **Compensation Design Surface** appears.  
  
2.  Add shapes to the **Compensation Design Surface** just as you would in the **Orchestration Design Surface**.  
  
     For more information, see [Adding Shapes to Orchestrations](../core/how-to-add-shapes-to-orchestrations.md).  
  
## See Also  
 [Making Orchestrations Transactional](../core/making-orchestrations-transactional.md)
