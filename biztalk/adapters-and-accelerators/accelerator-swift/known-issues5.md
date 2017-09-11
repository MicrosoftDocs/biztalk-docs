---
title: "Known Issues5 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "troubleshooting, known issues"
  - "BizTalk Accelerator for SWIFT, known issues"
  - "known issues"
ms.assetid: 0f1ec7dd-9e74-479a-bdc8-ab9c4397c992
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues
This section contains useful information that may help you avoid errors with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]. The known issues are grouped into the following areas:  
  
## Message Repair and New Submission

#### Printing of a repair document is recorded in the history log even if canceled  
 If you run the Print command for a document in the Repair Inbox, and then cancel the printing, the printing is still entered into the history log. This occurs when you open the document to be repaired in its [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, click the Print command on the File menu, and then click Cancel in the Print dialog box. You should ignore the entry in the history log.  
  
#### A duplicate signature can cause an XLANG/s error message  
 When a verifier uses the same certificate as a repairer, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] suspends the message and indicates in an error message that duplicate signatures are not allowed. However, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] also generates another error message with an event source of XLANG/s, indicating that the XLANG/s service has been suspended. You can ignore this message.  
  
#### Message size can affect repair performance  
 If you attempt to repair an unusually large XML file, system performance can significantly degrade when you open the XML file in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for the message type. Memory consumption may increase, CPU consumption may decrease, and the process may fail with an error indicating that not enough storage was available to complete the operation.  
  
#### The last signature used to sign a message successfully will be authenticated by Authenticate Signatures  
 Clicking the Authenticate Signatures button on an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form validates the signature for the stage that you are in only if you have already signed the form. Otherwise, it validates the signature for the previous stage, if there was one, and posts the following error:  
  
 The signing user is not correctly configured for the <stage_name> role in department <department_name>.  
  
 For example, suppose that you are in an approve stage immediately after a verify stage. If you have not yet signed the form as the approver, and you click Authenticate Signatures, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] authenticates the signature that the verifier used, not your approver's signature, and posts the preceding error.  

#### A4SWIFT cleanup tool doesn’t delete templates  
 The A4SWIFT cleanup tool doesn’t performs the following operations:  
  
-   Removes all MT templates from MRSR site  
  
-   Removes all agreements and partner profiles from MRSR site  
  
-   Removes all users, roles, and departments  
  
-   Unregisters the A4SWIFT BizTalk Server from the MRSR site  
  
#### The A4SWIFT_MRSRDepartment property is set to an empty string for a message that did not parse  
 When the message-repair orchestration routes to the MessageBox an unparsed message that has been fixed, it will set the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRDepartment property to an empty string and promote it. A send port will not be able to subscribe on this property.  
  
#### Cannot save a department if the SSO service has been stopped  
 If you try to add a department when the SSO service is stopped, you will receive an error indicating that the Primary SSO server \<machinename> failed. Check that SSO is configured and that the SSO service is running on that server.  
  
#### A department name must not contain the character "~"  
 A department name that contains the character "~" will cause issues with the A4SWIFT database.  
  
#### Signing Infopath forms  
 The signing of InfoPath forms needs to be done manually.  
  
## Security

#### Mixing trusted and untrusted hosts can enable spoofing  

 It may be possible to spoof SWIFT-bound messages from other non-trusted [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] host applications. This is only a problem when running in mixed-trust mode (when trusted hosts and untrusted hosts run applications in the same [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] group). You can mitigate this risk by using party-resolution pipeline components to identify the source of the SWIFT-bound message. This is not necessary when running in a fully trusted environment or for the majority of usage scenarios. You should follow the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] guidelines for building secure applications when mixing trusted and untrusted hosts. 
 
## Miscellaneous

#### The CacheEntries setting may be reset by a Setup program, affecting performance  
 The CacheEntries registry key determines the maximum number of rulesets cached by the Business Rule Engine Update service. The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Setup program sets CacheEntries to 32 by default. The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Setup program changes HKEY_LOCAL_MACHINE\SOFTWARE\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]\BusinessRules\3.0\CacheEntries to 512 for optimum performance. However, in certain circumstances, CacheEntries may be reset automatically. This may affect system performance.  
  
 Rule Engine updates may change CacheEntries from 512 to 32. After installing a Rule Engine update, manually reset CacheEntries to 512, if necessary.  
  
 Even though the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Setup program sets CacheEntries from 32 to 512, uninstalling [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not reset CacheEntries from 512 to 32.  
  
 For more information, see the "Rule Engine Configuration and Tuning Parameters" topic in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.  
  
#### Building a pipeline project may result in a large number of warnings  
 When you add the SWIFT assembler to a send pipeline, or the SWIFT disassembler to a receive pipeline, and then build the pipeline project containing those pipelines, you may receive a series of warnings related to the pipeline components. These warnings indicate that Visual Studio could not find dependencies. You can correct the condition leading to these warnings by changing the Copy Local property of the SWIFTAsm or SWIFTDasm assembly in the reference folder, as follows:  
  
1.  In Solution Explorer of Visual Studio, expand your pipeline project, and then expand the **References** node.  
  
2.  Under the References node, select the **SWIFTAsm** assembly and/or the **SWIFTDasm** assembly.  
  
3.  In the Properties pane, change the value for the **Copy Local** property to **False**.  
  
4.  Right-click your pipeline project, and then click **Build**.  
  
    > [!NOTE]
    >  You should not see any warnings about dependencies not being found.   