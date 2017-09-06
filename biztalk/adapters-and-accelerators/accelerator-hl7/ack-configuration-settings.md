---
title: "ACK Configuration Settings | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "acknowledgements, configuring"
  - "configuring, acknowledgements"
ms.assetid: 46e92560-7b1e-4d53-9de8-8ded4de90695
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ACK Configuration Settings
The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] parser generates acknowledgments based on Trading Partner Management (TPM) settings. The acknowledgment (ACK) settings are dependent on partner information. Schema type is not used. When [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives an ACK message with the MSH15 field containing AL, SU or ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] may send an ACK for this message based on the result of parsing the ACK header and TPM configuration. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] retrieves the partner ACK settings and returns one of the following five values:  
  
> [!NOTE]
>  The HL7 specification mandates that you use items 1 through 4 and to populate the MSH15 field of an ACK message that you generate. Item 5 is [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-specific and denotes not to generate an ACK.  
  
1.  AL – Always  
  
2.  NE – Never  
  
3.  SU – Success  
  
4.  ER – Error  
  
5.  NO – Do not generate an ACK  
  
## ACK configuration inconsistency  
 In the case of inconsistency between the ACK configuration user interface settings and values inside the message instance MSH15 and MSH16 fields, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK when one of the two ACK generation triggers require it. In the case of other inconsistencies, the data in the instance will override the setting in the configuration user interface.  
  
## See Also  
 [Configuring Message Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md)   
 [Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)