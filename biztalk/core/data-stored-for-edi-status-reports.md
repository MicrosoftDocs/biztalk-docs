---
title: "Data Stored for EDI Status Reports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec66e4d7-2694-499f-a60c-2f80fe643e12
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Stored for EDI Status Reports
Two levels of reporting are available in EDI status reporting: the first if the **Turn ON Reporting** property is selected for an agreement, and the second if the **Store transaction set/payload reporting** property is selected for an agreement. These properties are available in the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box.  
  
## Data Stored If EDI Reporting Is Activated  
 If the **Turn ON Reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will keep a record of all sent or received interchanges, technical acknowledgments, and functional acknowledgments.  
  
 For a received interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stores the following information:  
  
- A record of all received interchanges. This is the first information displayed in the status reporting UI for EDI.  
  
- A record of all transaction sets contained in the interchange. This does not include all the details that are stored when transaction-set storage is enabled.  
  
- A record of all Technical acknowledgments present in the received interchange  
  
- A record of all Functional acknowledgments present in the received interchange  
  
  > [!NOTE]
  >  If an interchange has multiple functional groups, multiple functional acknowledgments will be stored in the status reporting UI. However, if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives duplicate functional acknowledgments for a group, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store only the last functional acknowledgment in the status reporting UI.  
  
- Whether a technical acknowledgment needs to be generated for the received interchange  
  
- Whether functional acknowledgments need to be generated for the received transaction sets  
  
  For a sent interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stores the following information:  
  
- A record of the sent interchange  
  
- A record of all transaction sets contained in the interchange  
  
- A record of all Technical acknowledgments present in the sent interchange  
  
- A record of all Functional acknowledgments present in the sent interchange  
  
  EDI status reporting UI correlates these records to display complete information. For example, if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an interchange, and a technical acknowledgment and a functional acknowledgment need to be sent to the sender of the original message, you can easily find this information in the status reporting UI.  
  
## Data Stored If Transaction Set Storage Is Enabled  
 If the **Store message payload for reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store details of all transaction sets found in a sent or received interchange. This level of status reporting implements all of the first-level reporting performed if EDI reporting is activated, plus transaction-set specific information. The EDI receive pipeline and send pipeline make entries in the BAM database for each incoming and outgoing Group/Transaction Set (while the "**Store message payload reporting** property is selected). If the interchange is rejected, no entry is made.  
  
 For a sent or received interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stores the following information:  
  
-   The transaction set content. In the status reporting UI, you can look at the transaction sets contained in an interchange, and then view the actual transaction set content.  
  
-   More detailed information about a transaction set, including the following:  
  
|||  
|-|-|  
|Information|Field or Value|  
|ApplicationSender|(GS02 or \<UNG2.1(UNG2.2)\>|  
|ApplicationReceiver|GS03 or \<UNG3.1(UNG3.2)\>|  
|GroupDate|GS04 or UNG2.4|  
|GroupTime|GS05 or UNG2.5|  
|TransactionSetId|ST01 or  UNH2.1 (AN string)|  
|InterchangeControlNo|ISA13|  
|GroupControlNo|GS06|  
|BtsDocType|NameSpace + Root node name|  
|TransactionSetControlID|ST02 or UNH1|  
|TransactionSetStatus|Accepted, AcceptedWithError, or Rejected|  
|Direction|Send or Receive|  
|BtsProcessingTime|On receive side: BTSReceiveTime (local time) as stamped in the Pipeline<br /><br /> On send side: BTSSendTime as (local time) stamped on the envelope by the ASM component|  
|BTS.MessageId|On receive side: BTSMessageId from message properties<br /><br /> On send side:<br /><br /> For single Transaction Set: BTSMessageId<br /><br /> For outbound batch: TransactionSet BTSMessageId for each individual message in batch (not the BTSMessageId for the batch message) **Note:**  Storage only – will not be displayed in UI.|  
  
## See Also  
 [Data Stored for EDI and AS2 Status Reports](../core/data-stored-for-edi-and-as2-status-reports.md)   
 [Data Stored for Batching Status Reports](../core/data-stored-for-batching-status-reports.md)   
 [Data Stored for AS2 Status Reports](../core/data-stored-for-as2-status-reports.md)