---
title: "Status Report Data Stores | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6cd40ce8-1ac6-43b4-9cef-7cd045e8893c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Status Report Data Stores
Status reporting tracking data is stored in the BAM Primary Import database. A number of tables in this database are used for EDI and AS2 message data, including tables starting with dbo.bam_AS2, dbo.bam.batching, dbo.bam.InterchangeStatusActivity, and others. Status data is stored in the Primary Import even if EDI reporting is disabled. You will only be to view and query this data in the status reporting UI if status reporting is activated.  
  
 If you enable storage of message data for non-repudiation purposes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store the EDI and/or AS2 data in the EDI Message Content table of the BizTalk tracking database (BizTalkDTADb). If you enable storage of message contents for viewing details of the payload (by selecting the **Store message payload for reporting** agreement property in the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box), [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will also store the transaction sets in this table.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] archives and purges data from the BAM Primary Import and BizTalkDTADb databases. The tables in the databases are cleaned out according to a regular schedule.  
  
> [!NOTE]
>  The BAM Primary Import and DTA DB databases could be out of synch if each has a different interval for archiving.  
  
 EDI and AS2 status reporting may have an impact upon performance. For more information, see "Performance Considerations for EDI and AS2 Status Reporting" in [Known Issues with EDI and AS2 Performance](../core/known-issues-with-edi-and-as2-performance.md).  
  
## See Also  
 [How Data Is Stored for EDI and AS2 Status Reports](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)