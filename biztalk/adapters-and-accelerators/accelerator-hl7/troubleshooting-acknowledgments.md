---
description: "Learn more about: Troubleshooting Acknowledgments"
title: "Troubleshooting Acknowledgments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "acknowledgements, troubleshooting"
  - "troubleshooting, acknowledgements"
ms.assetid: faed356e-f5fc-4920-a9f9-82eca0ad7d67
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Acknowledgments
Addresses issues related to [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] acknowledgments.  
  
## Acknowledgments are not generated  
 There are several potential causes for acknowledgments (ACKs) not being generated or received. Review the following list of potential problems.  
  
### Symptom  
 Acknowledgments are not generated when you update party information in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer to generate acknowledgments.  
  
**Possible cause** : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] caches and refreshes party configuration information every 15 minutes.  
  
**Resolution** : Wait for at least 15 minutes for the cache to refresh, or restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for changes to take effect immediately.  
  
### Symptom  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not generate ACKs and event errors appear in the event log.  
  
**Possible cause** : An ACK cannot be generated when a batch in/batch out message contains an empty FHS11 field.  
  
**Resolution** : Ensure that your messages have a correctly formatted and populated FHS11 field.  
  
### Symptom  
 Your application cannot generate or receive an ACK.  
  
**Possible cause** : Incorrect information in the MSH3 field of your message prevents [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] from sending the message ACKs.  
  
**Resolution** : Ensure that your messages have a correctly formatted and populated MSH3 field.  
  
## Acknowledgments are suspended or not routed to the send party  
  
### Symptom  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends messages to a two-way adapter without generating acknowledgments.  
  
**Possible cause** : The message subscription is not configured correctly.  
  
**Resolution** : Ensure that message subscriptions are present and configured correctly.  
  
## Suspended acknowledgments  
  
### Symptom  
 Acknowledgments are suspended with the error message "Delimiter found in the field" when you have configured the party to have encoding characters containing delimiter characters such as @-!$.  
  
**Possible cause** : The message contains characters such as a period (.) or a hyphen (-). When generating the ACKs, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] includes "." and "-" for the timestamp value.  
  
**Resolution** : Disable validation in the send pipeline to avoid these errors.  
  
## BizTalk Server generates an error about missing ACK when using 2-way MLLP adapter  
  
### Symptom  
 You get the following or similar error in the Event Log:  
  
 "Unable to receive ACK from network due to error "Exception from HRESULT: 0xC0C01662""  
  
**Possible cause** : You are using 1-way receive and 2-way send port, so BizTalk does not have a corresponding Receive port to return the message received from the 2-way Send port.  
  
**Resolution** : This is by design, and you can ignore the error message.  
  
## See Also  
[Troubleshooting and known issues in HL7](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)
