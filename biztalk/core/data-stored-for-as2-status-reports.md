---
title: "Data Stored for AS2 Status Reports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6aa4077-3768-436b-99b9-d203a86a7e69
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Stored for AS2 Status Reports
Two levels of reporting are available in AS2 status reporting: the first if the **Turn ON Reporting** property is selected for an agreement (from the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box), and the second if a non-repudiation database storage property is selected for an agreement.  
  
## Data Stored If AS2 Reporting Is Activated  
 If the **Turn ON Reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will keep a record of all sent or received AS2 messages and MDNs.  
  
 For a received AS2 message, BizTalk Server will store the following information:  
  
- A record of the AS2 message.  
  
  For a received or sent MDN (synchronous or asynchronous), BizTalk Server will store the following information:  
  
- A record of the MDN.  
  
  The status reporting UI enables correlation of the AS2 message record to the appropriate MDN record.  
  
## Data Stored If Resend AS2 Message If MDN Not Received Is Enabled  
 If the **Resend AS2 message if MDN not received** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will record the following information:  
  
-   Time of each resend attempt  
  
-   Status of each resend attempt  
  
-   Index of each resend attempt  
  
## Data Stored If Non-Repudiation Database Storage Is Enabled  
 Non-repudiation database storage is enabled by the following agreement properties is selected:  
  
- NRR enabled for outbound encoded AS2 messages  
  
- NRR enabled for outbound decoded AS2 messages  
  
- NRR enabled for inbound MDN  
  
- NRR enabled for inbound encoded AS2 messages  
  
- NRR enabled for inbound decoded AS2 messages  
  
- NRR enabled for outbound MDN  
  
  If one or more of the above properties is selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store the following information:  
  
- The content of any AS2 message and the content of any MDN (with or without AS2 headers).  
  
## Data Stored For EDI Over AS2  
 If the **Turn ON Reporting** property is selected both for an EDI agreement as well as an AS2 agreement, then you can correlate an AS2 message record (containing EDI payload) with an EDI message record.  
  
 If transaction set storage is enabled, you can display transaction set details and AS2 message content details in the status reporting UI.  
  
> [!NOTE]
>  You must use the AS2EdiReceive or AS2EdiSend pipeline to have access to these reports.  
  
## See Also  
 [Data Stored for EDI and AS2 Status Reports](../core/data-stored-for-edi-and-as2-status-reports.md)   
 [Data Stored for EDI Status Reports](../core/data-stored-for-edi-status-reports.md)   
 [Data Stored for Batching Status Reports](../core/data-stored-for-batching-status-reports.md)