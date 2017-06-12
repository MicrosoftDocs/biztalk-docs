---
title: "Troubleshooting Other Issues | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "troubleshooting"
ms.assetid: 1f115f64-45ce-445d-ab18-092f4a6a232c
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Other Issues
Addresses other issues related to [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].  
  
## Message rejected by the BTAHL7 engine  
  
### Symptom  
 Messages are randomly rejected by the message engine.  
  
**Possible Cause** : According to the HL7 standard, enumeration values for table 0338 contains the "L&I" value. Field 6 of the PRA segment may contain this value. Since [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] treats the "&" character as a delimiter, the message is rejected.  
  
**Resolution** : There are three potential resolutions for this issue:  
  
1.  In the message instance, handle the "&" character through an escape sequence, such as using the character combination L\T\I.  
  
2.  Add an enumeration value of "LI" at PRA 6 in the schema and use this value instead in the message instance.  
  
3.  Use a completely different subcomponent separator in MSH2; however, this particular solution may not be practical depending upon your environment.  
  
## Cannot edit the HL7 schema using Visual Studio  
  
### Symptom  
 Cannot edit the HL7 schema using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
**Possible Cause** : [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] does not support some HL7 schemas.  
  
**Resolution** : Use other editors, such as [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Notepad, to edit HL7 schemas.  
  
## Message handling fails with no errors logged  
  
### Symptom  
 The system processes messages without logging error messages or placing messages in the suspended message queue.  
  
**Possible Cause** : The **HeaderSpecType** and **DocumentSpecType** property values are case-sensitive. When you deploy your pipelines, a typographical error in these names can cause messages to be mishandled and dropped with no errors logged.  
  
**Resolution** : Observe case-sensitivity when using the **HeaderSpecType** and **DocumentSpecType** property value names.  
  
## Message header fields are not validated correctly  
  
### Symptom  
 Validation of a header field failed.  
  
 Reason: The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer validated a promoted property, not the actual header-field context property.  
  
**Possible Cause** : A change occurred to the promoted property corresponding to the header through an orchestration or a map.  
  
**Resolution** : The context properties of message headers MSH1, MSH2, and MSH5{1-3} need to be updated so that they are in synchronization with the data.  
  
## The MLLP adapter is not removed during uninstall  
  
### Symptom  
 The BTAHL7 setup program did not remove the MLLP adapter during uninstallation of BTAHL7.  
  
**Possible Cause** : There was a receive location or send port with a transport type of MLLP. BTAHL7 setup cannot remove the MLLP adapter if it is being referenced in any of the BizTalk Server projects.  
  
**Resolution** : After uninstallation of BTAHL7 has completed, do the following:  
  
1.  In the BizTalk Server Administration Console, remove all receive locations and send ports that have a transport type of MLLP, or change the transport type of the receive locations or send ports to another type.  
  
2.  In the Administration Console, delete the MLLP adapter.  
  
3.  Restart the host instance.  
  
## BTAHL7 cannot be uninstalled if BizTalk Server has already been uninstalled  
  
### Symptom  
 Uninstalling [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] results in the following error:  
  
`A network error while attempting to read from file C:\Windows\Installer\Microsoft BizTalk <version\> Accelerator for HL7.msi`
  
**Possible Cause** : [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] was uninstalled before uninstallation of [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] was attempted. You must uninstall [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] before uninstalling [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].  
  
**Resolution** : Reinstall [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], then uninstall [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], and then uninstall [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].  
  
## Messages are still sent after the applicable MLLP send port has been stopped  
  
### Symptom  
 After you stop an MLLP send port, the messages that are sent through that send port do not stop, but continue to be sent.  
  
**Possible Cause** : When you stop a send port, the connection remains established until it is removed by stopping the BizTalk host. As a result, messages are still sent after the send port has been stopped. This occurs because Biztalk Server does not call into the MLLP adapter during start or stop of the send port. BizTalk Server calls into the MLLP adapter only during the start and stop of the host service.  
  
**Resolution** : You can remove the connection and stop transmission of messages by stopping the host instance that is the send handler for the send port that you stopped. However, stopping that host instance might affect other messages that you do not want to stop. If you know that this is the case, you should configure the send port differently when you create it. You should create another host instance to serve as the send handler for only this MLLP send port (or a subset of your send ports). You can then stop transmission of messages from this send port by stopping this host instance. This will then not affect transmission of other messages on other send ports that use other send handlers.  
  
## See Also  
 [Troubleshooting and known issues in HL7](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)