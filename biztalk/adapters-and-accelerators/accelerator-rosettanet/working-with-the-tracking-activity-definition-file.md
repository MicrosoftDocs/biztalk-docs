---
title: "Working with the Tracking Activity Definition File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tracking, activity definition file"
  - "activity definition file"
  - "activity definition file, about activity definition file"
  - "tracking, managing views"
  - "activity definition file, activity fields"
ms.assetid: 0592a844-aad7-4054-b1e7-344f1086f0b1
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Working with the Tracking Activity Definition File
The activity definition file contains information about the tracking process and message activities in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] uses this file to manage data tracking in BizTalk Business Activity Monitoring (BAM). The definition file is an XML file (Tracking.xml) that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] setup installs in the \<*drive*\>:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAMTracking folder. The activities defined in Tracking.xml may be sufficient for your purposes.  
  
 For more information about the tracking activities, views, and tables, see [Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md). For more information about BAM, see "Business Activity Monitoring (BAM)" in BizTalk Server Help.  
  
## Managing Tracking Views  
 You do not use the BizTalk Tracking Profile Editor with [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] tracking. The tracking points are not customizable; do not change activity definitions. However, you can manage BAM views and deployment. To do so, you modify an [!INCLUDE[btsExcel](../../includes/btsexcel-md.md)] spreadsheet (Tracking.xls) that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] setup installs in the \<*drive*\>:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking folder. For more information, see "Managing Tracking Views" below.  
  
 If the views defined in Tracking.xml are not sufficient for your needs, you can define different views of the information tracked in BAM as follows.  
  
#### To create different tracking views  
  
1. Click **Start**, and then click **Run**. Enter **cmd** in the Open text box of the Run dialog box, and then click **OK**. In the command line dialog box, enter the following code to undeploy tracking.xml, then click **OK**:  
  
   ```  
   cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
   bm remove-all  -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking\<filename\>.xml"  
   ```  
  
2. In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to *\<drive\>*:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAM Tracking. Double-click Tracking.xls.  
  
3. Create a new view in Business Activity Monitoring. For information about how to do so, see "Managing Business Activity Monitoring" in BizTalk Server Help.  
  
4. Click **BAM**, and then click **Export XML**. Move to the desired location, enter a file name (other than Tracking.xml), and then click **Save**.  
  
   > [!IMPORTANT]
   >  When you define new tracking views in a tracking XLS file, and export an XML file from the tracking XLS file, some of the new field names may be slightly modified. Correct this by verifying the fields in your customized tracking XML file against the standard tracking.xml field installed by BTARN setup.  
  
5. Deploy the new tracking XML file. To do so, click **Start**, and then click **Run**. Enter **cmd** in the Open text box of the Run dialog box, and then click **OK**. In the command line dialog box, enter the following code to deploy your new tracking file, then click **OK**. It is recommended that you rename the tracking XML file so that you do not overwrite the default tracking.xml file.  
  
   ```  
   cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
   bm.exe deploy-all -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2030 Accelerator for RosettaNet\BAMTracking\<filename\>.xml"  
   ```  
  
   The information tracked in BAM does not include the message content, because that is stored in a [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] database.  
  
   You can manage deployment of BAM tracking by using the Business Activity Monitoring Management Utility. For more information about this utility, see "Using the Business Activity Monitoring Management Utility" in BizTalk Server Help.  
  
## Activity Fields  
 The fields of the message activity in the activity definition file are the following:  
  
- ActivityName  
  
- Category  
  
- ContentKey  
  
- DestinationPartyName  
  
- ErrorDescription  
  
- HasError  
  
- InReplyToMessageID  
  
- IsReceived  
  
- MessageTrackingID  
  
- NoFPipInstance  
  
- PipCode  
  
- PipInstanceID  
  
- PiPVersion  
  
- SourcePartName  
  
- Timestamp  
  
  The fields of the process activity in the activity definition file are the following:  
  
- EndTime  
  
- InitiatorPartyName  
  
- IsInitiatorRole  
  
- PipCode  
  
- PipInstanceID  
  
- PipName  
  
- PipVersion  
  
- ResponderPartyName  
  
- StartTime  
  
- Status  
  
## See Also  
 [Enhanced Tracking](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)   
 [Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md)