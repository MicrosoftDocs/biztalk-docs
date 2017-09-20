---
title: "Troubleshooting Batching | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "batching, troubleshooting"
  - "troubleshooting, batching"
ms.assetid: f47e1a16-47fd-4bd8-8dad-fcdba31a833e
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Batching
Addresses issues related to [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batching.  
  
## Error activating batch  
  
### Symptom  
 Unable to activate a batch. You get a general network error.  
  
**Possible Cause** : [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] was restarted, but [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer was not.  
  
**Resolution** : Restart [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.  
  
## Messages are not batched when the target namespace is not the default  
  
### Symptom  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] is not batching messages.  
  
**Possible Cause** : Source and destination parties are not in the same schema namespace.  
  
**Resolution** : Source and destination parties must use the same schema namespace if validation is required. Ensure the source and destination parties are using the same schema namespace.  
  
## See Also  
 [Troubleshooting and known issues in HL7](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)