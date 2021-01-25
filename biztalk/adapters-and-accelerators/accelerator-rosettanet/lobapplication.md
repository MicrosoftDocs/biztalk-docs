---
description: "Learn more about: LOBApplication"
title: "LOBApplication | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "trading partners, submitting actions"
  - "LOBs, submitting actions"
  - "LOBApplication utility"
  - "trading partners, response messages"
  - "LOBs, LOBApplication utility"
  - "LOBs, response messages"
ms.assetid: ad5986af-4175-49cd-806b-04e1fde63f55
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# LOBApplication
You use the LOBApplication utility to submit an action or response message to a trading partner, simulating an actual line-of-business (LOB) desktop program.  
  
 Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] provides sample messages in the \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder.  
  
## Location in SDK  
 \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication  
  
## Running LOBApplication  
  
#### To run LOBApplication  
  
1.  In Windows Explorer, move to \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\\.  
  
2.  Double-click **LOBApplication.exe**, and then press ENTER.  
  
     The pages that follow prompt you for the information that is required to run the utility.  
  
## Syntax for LOBApplication  
 Use the **LOB Application Proxy** page to specify home and partner names, Partner Interface Process (PIP) properties, and message properties for the message sent by the LOBApplication utility.  
  
 The following table describes how to use each field on the **LOB Application Proxy** page.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Home Profile Name**|Type the name of the home organization (source party).|  
|**Trading Partner Name**|Type the name of the trading partner (destination party).|  
|**PIP Name**|Type the display code of the PIP, for example, type **3A2**. This value is case-sensitive.|  
|**PIP Version**|Type the version of the PIP, for example, type **V02.00**. This value is case-sensitive.|  
|**PIP Instance ID** (optional)|Type an alphanumeric instance ID for the PIP, for example, type **STD_3A2_V02.02**. Avoid special characters. The ID should be unique per partner and per PIP code. For messages that are marked as action messages, if the Instance ID is empty, the LOBApplication utility uses a generated HUID value for the PIP Instance ID. **Note:**  When you select **Response** in the **Message Category**, you must type the PIP Instance ID in this field.|  
|**File Name**|Click the ellipsis button (...), go to the folder that contains the PIP instance file, and then click the PIP instance file.|  
|**Message Category**|Select the type of message (**Action** or **Response**).|  
|**Attachments**|Click **Add**, move to the folder that contains the attachment file, and then click **Open**.|  
|**Submit Message**|Click to send the message.|  
|**Status**|Read the status of the action in this field.|  
  
## Remarks  
 The LOBApplication utility creates a message with the properties specified, and sends it to the trading partner. This utility writes the service content data in the message to the BTARNDATA database, in the MessageFromLOB table. This utility simulates sending an action message.  
  
 The sample messages in the SampleInstances folder under the LOBApplication folder in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK are preconfigured to assume the following Global Business Identifiers (GBIs): 123456789 for the home organization and 987654321 for the partner organization. You must change the sample messages in a text editor to use other GBIs.  
  
 You use the LOBApplication utility to simulate a line-of-business desktop program submitting a message. You use the LOBWebApplication utility to simulate a line-of-business Web application submitting a message.  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [LOBWebApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobwebapplication.md)
