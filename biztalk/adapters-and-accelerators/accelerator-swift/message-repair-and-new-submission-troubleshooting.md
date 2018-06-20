---
title: "Message Repair and New Submission Troubleshooting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "troubleshooting, Message Repair and New Submission"
  - "Message Repair and New Submission, troubleshooting"
ms.assetid: bb07a286-6f02-4639-b5fa-a3647e356ac8
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Repair and New Submission Troubleshooting
## A repaired message cannot be submitted if the envelope schema is not deployed  
  
### Symptom  
 When you attempt to submit a message that you have repaired, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] posts the following message:  
  
 "The adapter failed to transmit message going to send port "<http://mrsrtest:80/StsWebReceive/default.aspx?PartnerId=Unparsed&FolderType=MessagesInbox>". It will be retransmitted after the retry interval specified for this Send Port. Details:"80131600". For more information, see Help and Support Center at [http://go.microsoft.com/fwlink/?LinkId=142493](http://go.microsoft.com/fwlink/?LinkId=142493).  
  
### Possible Cause  
 The envelope schema is not deployed. This is true for any MT*xxx* message or any message that has failed parsing.  
  
### Solution  
 Deploy an envelope schema for each message schema that you are using (\<drive\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack \SWIFT Messages\ A4SWIFT-SRG\<version\>\Category n\MTxxx.xsd) and for unparsed envelope schema (\<drive\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack \SWIFT Messages\ A4SWIFT-SRG\<version\>\ Unparsed Message\EnvelopeUnparsedMessage.xsd). For more information, see [Deploying A4SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).  
  
## You cannot submit a fixed unparsed message from a MRSR site library named other than "Unparsed"  
  
### Symptom  
 When you try to submit an unparsed message that you have fixed from a MRSR site document library that is not named "Unparsed", the operation fails.  
  
### Possible Cause  
 A4SWIFT cannot successfully submit a message from a library that is not named "Unparsed". If you have an existing "Unparsed" document library in MRSR site before you install the MRSR (message repair) feature, A4SWIFT setup will create a library for unparsed messages entitled "Unparsed" with a suffix. When it receives a message that A4SWIFT could not parse, it will route the message to that library that it created. However, when you try to submit a message from that library, the operation will fail.  
  
### Solution  
 Remove the MRSR feature, delete the Unparsed library, and then reinstall the MRSR feature.  
  
## Cannot loop back a message in a two-stage workflow  
  
### Symptom  
 If you reject a message in the Repair stage of a workflow that has only a Create stage and a Repair stage, the submission fails. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] routes the message back to the MessageBox and posts the following error message:  
  
 "Could not reset to the first stage in the workflow."  
  
### Possible Cause  
 Message loopback is not supported for a workflow that has only a Create stage and a Repair stage.  
  
### Solution  
 Add another stage to the two-stage workflow, or cancel the submission.  
  
## Cannot open a message in the repair inbox in MRSR  
  
### Symptom  
 When you try to open a message in the repair inbox in MRSR, you receive the following error message in a popup:  
  
 "Cannot open database requested in login 'A4SWIFT'. Login fails. Login failed for user 'NT AUTHORITY\NETWORK SERVICE'.  
  
### Possible Cause  
 The login account for the web application that the A4SWIFT_MRSR web service runs under is Network Service, not a local or domain account that is in the A4SWIFT Users group.  
  
### Solution  
 Change the login account for the web application that the A4SWIFT_MRSR web service runs under.  
  
##### To change the login account for the web application that the A4SWIFT_MRSR web service runs under  
  
1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  In IIS Manager, expand the ***\<server name\>* (local computer)** node, the **Application Pools** node and the **Web Sites** node. Under the Web Sites node, expand the **Default Web Site** node.  
  
3.  Under the Default Web Site node, right-click **A4SWIFT_MRSR**, and then click **Properties**.  
  
4.  In the A4SWIFT_MRSR Properties dialog box, note the Application pool.  
  
5.  In the IIS Manager dialog box, under the Application Pools node, right-click the application pool for A4SWIFT_MRSR, and then click **Properties**.  
  
6.  In the \<application pool name\> Properties dialog box, click the **Identity** note. If **Predefined** is clicked and **Network Service** is selected, click **Configurable**, enter your local or domain account, and then enter your password. Click **OK**.  
  
## A message created in MRSR site on a localized computer is not processed  
  
### Symptom  
 When a user working on an English version of A4SWIFT that is running on a localized platform creates a message in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form in MRSR, and submits the message successfully, the message appears to be consumed by the Message Repair and New Submission orchestration, but is not successfully processed. The message is submitted to the outbox, but is not picked up by the BizTalk adapter. No error or warning is posted in the Event Viewer, and there is no record of a running orchestration instance in HAT.  
  
### Possible Cause  
 The path entered as the URI for the STS.Outbox receive location contains the English name, not the localized name.  
  
### Solution  
 Change the URI address for the STS.Outbox receive location as follows:  
  
1.  In the BizTalk Server 2009 Administration Console, expand the **BizTalk Group**, **Applications**, and **BizTalk Application 1 nodes**.  
  
2.  Click **Receive Locations**.  
  
3.  Double-click **Sts.Outbox.Location**.  
  
4.  In the Receive Location Properties dialog box, click **Configure**.  
  
5.  In the Transport Properties dialog box, replace the value for **SharePointSite URL** with the localized equivalent.  
  
6.  Click **OK**, and then click **OK**.  
  
## Removing a role while it is processing a message results in incomplete removal of documents and artifacts  
  
### Symptom  
 When you remove a role in the Profile Web Client, a dialog box is posted indicating that all documents and artifacts associated with the role will be removed. However, the role is not removed from the department in the A4SWIFT Management Console, and the role's document folders (Inbox and Sent Items) are not removed from MRSR. The party, send port, and agreement associated with the role are removed, and the profile of the role is undeployed.  
  
### Possible Cause  
 A message is still in the role's inbox in MRSR, and the message is open in its [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form.  
  
### Solution  
 Manually delete the message from the MRSR site inbox, and then delete the document library that is associated with the role that you were removing. Close the form and remove the role again.  
  
## Message processing fails as a result of an error in the BIC Master Policy  
  
### Symptom  
 When you submit a message for processing, you receive the following error:  
  
 "An error occurred while executing the BicMasterPolicy. Check the policy for valid values."  
  
### Possible Cause  
 The SQL Server name, BIC database name, and integrated security value in the BIC_Master_Policy.xml file in *\<drive\>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies are contained in double quotes. To enable BIC validation, you enter these strings in the default BIC_Master_Policy.xml file as described in [Enabling Validation of Bank Identifier Codes](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md).  
  
### Solution  
 To repair the BIC master policy, proceed as follows:  
  
> [!NOTE]
>  For more information about deploying the BIC master policy, see [Deploying BRE Rules](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md).  
  
1.  In Business Rule Composer, undeploy Version 1.0 of the BIC_Master_Policy, and then delete the BIC_Master_Policy.  
  
2.  In a text editor, such as Notepad, open BIC_Master_Policy.xml in *\<drive\>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies. Remove the double quotes around the SQL Server name, BIC database name, and integrated security value.  
  
3.  In the Business Rules Engine Deployment Wizard, import BIC_Master_Policy.xml, and then deploy BIC_Master_Policy.xml.  
  
4.  In the Services MMC, restart the Rule Engine Update Service and the BizTalk Receive Host Service.  
  
## A4SWIFT will not be able to process an unparsed message without proper database permissions  
  
### Symptom  
 When you drop a message that A4SWIFT cannot parse, A4SWIFT is unable to process the message, but fails with an uncaught exception.  
  
### Possible Cause  
 There is a database permission issue. The Log On account for the BizTalk service, which by default is HostSvc, is not included in the A4SWIFT Administrators and A4SWIFT Users groups.  
  
### Solution  
 Add the Log On account for the BizTalk service to the A4SWIFT Administrators and A4SWIFT Users groups.  
  
## A timeout of the InfoPath repair form can result in two copies of a message in different stages of the repair workflow  
  
### Symptom  
 When you submit a message from an InfoPath form (for any workflow stage), if there is an error in submission of the form, the error could result in two copies of message. One message is still in the inbox for the current stages, and the other message is in the inbox for the next role in the workflow. Attempting to process these messages will result in the following:  
  
-   If you submit the message from the inbox for the next role of the workflow, the message will continue through the workflow.  
  
-   If you submit the message from the inbox for the current stage after the message submitted from the inbox of the next stage has completed processing, the message submitted from the current inbox will be suspended with a routing failure.  
  
-   If you submit the message in the inbox for the current stage before the message submitted from the inbox of the next stage has completed processing, the message submitted from the inbox for the current stage will be returned to the inbox for that stage, and you will receive the following error:  
    "Resetting workflow due to: either the message was tampered with or the user is invalid for this stage."  
    After this, if you submit the message from the inbox for the next stage, the workflow for it will also be reset. It will be returned to the inbox for the current stage and you will receive the above error.  
  
### Possible Cause  
 The InfoPath form has submitted the message to BizTalk Server via Microsoft Windows Sharepoint Services and a custom Web service that performs validations. Submitting a message is accomplished in multiple steps and these steps are not transactional, because Windows Sharepoint Services is not transactional. To accommodate this limitation, the MRSR orchestrations have built in recovery logic to detect and recover from errors arising from the message submission. The MRSR orchestrations always prevent duplicate messages being sent to SWIFT.  
  
### Solution  
 If this occurs, you should pick the message that is further along in the workflow and complete its workflow before attempting to process the other messages that are in the earlier stages of the workflow. After the message that is further along in the workflow has completed processing, you can dispose of the second message (which was suspended with a routing failure) as you see fit.  
  
 If the message that is further along in the workflow did not complete processing before you processed the second message, you should once again repair the message that is further along in the workflow in the repair InfoPath form, and then submit it. Allow it to complete processing, and then submit the second message. After the second message has been suspended, dispose of it.  
  
## A new submission with no verify stage will result in a suspended message  
  
### Symptom  
 When you submit a new message in a workflow that has no verify stage, the message is suspended.  
  
### Possible Cause  
 The lack of a verify stage results in a suspended message if A4SWIFT_MRSRLastStage is not set to Create.  
  
### Solution  
 Use a subscription of A4SWIFT_MRSRLastStage == Create to ensure that the message is routed properly.  
  
## Validation of message results a "parse error" in the InfoPath form task pane  
  
### Symptom  
 Validate Message button in the InfoPath form task pane shows “parse error” without any description.  
  
### Solution  
 Restart the MRSR web service or do iisreset.  
  
## Publishing an InfoPath form results an authorization error  
  
### Symptom  
 Publishing an InfoPath form gives authorization error.  
  
### Solution  
 Replace machine name by localhost in the MRSR site URL.  
  
## InfoPath form task pane shows HTML source code  
  
### Symptom  
 InfoPath form task pane shows HTML source code instead of Web controls.  
  
### Solution  
 Go to **Tools**-> **Security Tab** -> **Internet Zone**, and enable **Open file based on content not on extension** under Miscellaneous.  
  
## Profile Web Client website results an Authentication error  
  
### Symptom  
 Profile Web Client website displays Authentication error.  
  
### Solution  
 Run the **BTSharePointAdapterWSAppPool** and **DefaultAppPoolApplication** -> and pool in Internet Information Services(IIS) under the administrator account.  
  
## See Also  
 [Troubleshooting: Issues and Resolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)