---
title: "Troubleshooting Errors | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errors, troubleshooting"
  - "troubleshooting, errors"
ms.assetid: 08cc95a3-4be9-450f-a015-e031011158f7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Errors
This section addresses issues related to [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generated errors.  
  
## The MLLP adapter can run only on a single host instance  
  
### Symptom  
 You cannot enable a receive location with a transport type of MLLP and a different receive handler than another existing receive location. In addition, you cannot enlist and start a send port with a different send handler than another existing send port.  
  
**Possible Cause** : You can only use one MLLP receive (or send) handler on a single server. In addition, the URI designated for the receive location (or send port) (the Host name in the MLLP Transport Properties) must either be "localhost" or the server name where the host instance for the receive (or send) adapter handler is running.  
  
**Resolution** : Designate the same receive (or send) handler for all MLLP receive locations (or send ports) on a single server.  
  
## MSH and ACK schemas must be added to only one project  
  
### Symptom  
 When you attempt to build a project, you get one of the following errors:  
  
`Error: Cannot locate document specification as multiple schemas match the message type "http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF"`
  
`Schema http://microsoft.com/HealthCare/HL7/2X#MSH_24_GLO_DEF not found`
  
**Possible Cause** : The MSH and ACK schemas (MSH_25_GLO_DEF.xsd and ACK_24_GLO_DEF.xsd) have been deployed in multiple projects.  
  
**Resolution** : Ensure that MSH_25_GLO_DEF.xsd and ACK_24_GLO_DEF.xsd have been added to only one project.  
  
## Exception of type System.OutOfMemoryException has thrown an error in the Event Log  
  
### Symptom  
 You get the following or similar error in the Event Log:  
  
`Exception of type System.OutOfMemoryException has thrown an error.`
  
**Possible Cause** : While processing a large number of messages, some [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] engine components may exhibit memory leaks.  
  
**Resolution** : Restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
## Header serialization generates an error in the Event Viewer  
  
### Symptom  
 You get the following or similar error in the Event Log, even though the message in the Health and Activity Tracking (HAT) tool indicates success:  
  
`An error happened in the header during serialization.`
  
**Possible Cause** : The message header transformation value is not set correctly in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.  
  
**Resolution** : Verify MSH map values in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.  
  
## Duplicate Event ID 4133 serializer errors are logged  
  
### Symptom  
 Event ID 4133 – "Error happened in header during serialization" occurs twice for every instance of a message with a MSH11 value that is not valid.  
  
**Possible Cause** : An error occurred while processing two acknowledgments (Commit and Application ACKs) without duplicate errors in the Event Log. Instead, you receive one Event ID 4133 for each of the two ACKs. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] creates a log entry for each ACK it generates.  
  
**Resolution** : Ensure that your messages have a correctly formatted and populated MSH11 field.  
  
## Send pipeline generates an error when using the 2-way MLLP adapter  
  
### Symptom  
 You get the following or similar error in the Event Log:  
  
`There was a failure executing the send pipeline: "[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XPipelines.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2XSendPipeline" Source: "[!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fAsm" Send Port: "<*host name: port number*>" Reason: Message does not contain a part with name MSHSegment.`
  
**Possible Cause** : The receiving application does not respond with an Acknowledgment and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is expecting a response from the receiving application.  
  
**Resolution** : This is by design, and you can ignore the error message.  
  
## See Also  
 [Troubleshooting and known issues in HL7](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)