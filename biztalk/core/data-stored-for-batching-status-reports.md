---
title: "Data Stored for Batching Status Reports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d55aa0e1-095f-434e-8530-f1a946ad4430
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Stored for Batching Status Reports
When the **Turn ON Reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store the status of each batching instance. This property is in available in the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box. The status can be any of the following:  
  
- **Defined**: The batch instance is configured. The batch activation start date time is greater than the current date time. All batch parameters are defined, but the batch is not running (not accepting documents).  
  
- **Active**: The batch instance has been activated and is aggregating transaction sets. You can view the number of accepted/rejected transaction sets.  
  
- **Released**: The batch met the release criteria and was released into the MessageBox, but has not been released by the send pipeline, or that the batch was stopped before processing any messages.  
  
- **Completed**: The batch was sent by the EdiSend pipeline.  
  
  If the batch was sent by the EdiSend pipeline, you can correlate the batch record in the UI with a record of the sent Edi interchange, and view transaction set details.  
  
> [!NOTE]
>  There may be multiple batch instances with a status of Completed for a batch configuration.  
  
 **Correlating an Interchange with a Batch**  
  
 The BusinessMessageJournal BAM activity enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to correlate a received EDI interchange containing a transaction set with an outgoing batched interchange that contains the same transaction set. For information about how to implement and use this correlation information, see [Correlating an Incoming Transaction Set with an Outgoing Batch](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md).  
  
## See Also  
 [Data Stored for EDI and AS2 Status Reports](../core/data-stored-for-edi-and-as2-status-reports.md)   
 [Data Stored for EDI Status Reports](../core/data-stored-for-edi-status-reports.md)   
 [Data Stored for AS2 Status Reports](../core/data-stored-for-as2-status-reports.md)