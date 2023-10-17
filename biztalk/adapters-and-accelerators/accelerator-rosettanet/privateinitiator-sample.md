---
description: "Learn more about: PrivateInitiator Sample"
title: "PrivateInitiator Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f176566-2a71-487d-84c1-5e7767701e8b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# PrivateInitiator Sample
The PrivateInitiator.odx sample contains the code for the initiator private process installed by Microsoft® BizTalk Server. This is a generic private process that sends and receives RNIF service-content messages from the default SQL adapter-based send and receive ports.  
  
 By default, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs the sample in \<*drive*\>:\Program Files\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateInitiator.  
  
## Sample Contents  
 The initiator private process is the business process that is internal to the initiator. The private process provides back-end integration between the initiator public process and the back-end line-of-business program. The initiator private process communicates with the public process to initiate messages.  
  
 The initiator private process is unique for each implementation. You can customize the PrivateInitiator.odx sample for your purposes. You must be careful that you do not adversely affect the functioning of the initiator public process.  
  
 For more information, including a description of the message flow, see [Initiator Private Process](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md).  
  
## See Also  
 [Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [Private Processes](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)
