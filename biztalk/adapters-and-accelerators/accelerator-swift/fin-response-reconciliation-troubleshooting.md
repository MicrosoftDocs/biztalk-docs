---
title: "FIN Response Reconciliation Troubleshooting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FIN Response Reconciliation, troubleshooting"
  - "troubleshooting, FIN Response Reconciliation"
ms.assetid: f62326aa-9a4e-4941-a9bb-20bde980f99e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FIN Response Reconciliation Troubleshooting
## The FRR BAM view does not show the message type of a message  
  
### Symptom  
 The FRR BAM view in MRSR site does not show the message type for one or more messages. All other data for the message or messages is shown, and the message type is shown for instances of all other message types.  
  
### Possible Cause  
 The FRRMessageOut activity does not record the message type for F21 messages (ACKs/NAKs).  
  
### Solution  
 If you encounter this problem, interpret any message that does not have a message type listed in the FRR BAM view in MRSR site as an F21 message.  
  
## Deploying system-level schemas in a project generates an error  
  
### Symptom  
 When you attempt to deploy the system-level schemas in FrrSchemas.dll in a project, you receive an error. For a list of these schemas, see [FIN Response Types](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md).  
  
### Possible Cause  
 The system-level schemas in FrrSchemas.dll are already deployed in FrrSchemas.dll. Trying to deploy them again results in an error.  
  
### Solution  
 There is no need to deploy the system-level schemas in FrrSchemas.dll.  
  
## See Also  
 [Troubleshooting: Issues and Resolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)