---
description: "Learn more about: PrivateResponder Sample"
title: "PrivateResponder Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3137fadd-9582-4cc6-acfb-c44aca636950
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# PrivateResponder Sample
The PrivateResponder.odx sample contains the code for the responder private process installed by Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. This generic private process sends and receives RNIF service-content messages from the default SQL adapter-based send and receive ports.  
  
 By default, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs the sample in \<*drive*>:\Program Files\\Microsoft  BizTalk \<version> Accelerator for RosettaNet\SDK\PrivateResponder.  
  
## Sample Contents  
 The responder private process is the business process that is internal to the responder. The private process provides back-end integration between the responder public process and the back-end line-of-business program. The responder private process communicates with the public process to respond to messages.  
  
 The responder private process is unique for each implementation. You can customize the PrivateResponder.odx sample for your purposes. You must be careful that you do not adversely affect the functioning of the responder public process.  
  
 For more information, including a description of the message flow, see [Responder Private Process](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md).  
  
## See Also  
 [Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [Private Processes](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)
