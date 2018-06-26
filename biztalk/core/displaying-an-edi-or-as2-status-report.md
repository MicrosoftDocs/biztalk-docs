---
title: "Displaying an EDI or AS2 Status Report | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60968c3d-6329-411f-9f10-1dd4a6cc9d79
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Displaying an EDI or AS2 Status Report
When EDI and AS2 status reports are enabled, you will have access to the following status reports:  
  
|Type of Report|Higher-level status report|Lower-level status report|  
|--------------------|---------------------------------|--------------------------------|  
|EDI|EDI Interchange and Correlated ACK Status|- Interchange Status and ACK Details<br /><br /> - Transaction Set Details<br /><br /> - EDI Message Content|  
|EDI|Batch Status|-|  
|EDI|Interchange Aggregation Report|-|  
|EDI|Transaction Set Aggregation Report|-|  
|AS2|AS2 Message and Correlated MDN Status|AS2 Message Content|  
  
## Prerequisites  
 The following are prerequisites for performing the procedure in this topic:  
  
- You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to customize any of the status reports.  
  
- If you are logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group, you can display read-only status reports.  
  
## Display an EDI or AS2 status report  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **BizTalk Group** node.  
  
2. In the **Group Hub** tab of the **Group Overview** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, move to the bottom of the page.  
  
3. To display the **EDI Interchange and Correlated ACK Status** report, proceed as follows:  
  
   1.  Click **EDI Interchange and Correlated ACK Status** in the **EDI Status Reports** area of the **Group Hub** tab.  
  
   2.  To display details of an interchange and its correlated acknowledgments, right-click an entry in the query results of the **EDI Interchange and Correlated ACK Status** report, and then click **Interchange status and ack details**.  
  
   3.  To display details of a transaction set, close the Interchange status and ack details report, returning to the **EDI Interchange and Correlated ACK Status** details report. Right-click an entry in the query results, and then click **Transaction Set Details**.  
  
   4.  To display details about the headers and payload of a transaction set, right-click an entry in the **Transaction Set Details** report, and then click **View Transaction Set Content**.  
  
   5.  To display data about the interchange containing the transaction set, right-click an entry in the **Transaction Set Details** report, and then click **Interchange/ACK Status**. The interchange containing the transaction set will be highlighted in the Interchange/ACK Status report.  
  
4. To display the **Batch Status** report, proceed as follows:  
  
   1.  Click **Batch Status** in the **EDI Status Reports** area of the **Group Hub** tab.  
  
   2.  To display the completed batches associated with a batch entry in the **Batch Status** report, right-click the entry and then click **Completed Batches**.  
  
   3.  To display data about a completed batched interchange, right-click the interchange in the **Completed Batch** report, and then click **Interchange/ACK Status**. The entry for the batched interchange will be highlighted in the Interchange/ACK Status report.  
  
5. To display the **Interchange Aggregation Report**, proceed as follows:  
  
   -   Click **Interchange Aggregation Report** in the **EDI Status Reports** area of the **Group Hub** tab.  
  
6. To display the **Transaction Set Aggregation Report**, proceed as follows:  
  
   -   Click **Transaction Set Aggregation Report** in the **EDI Status Reports** area of the **Group Hub** tab.  
  
7. To display the **AS2 Message and Correlated MDN Status** report, proceed as follows:  
  
   1.  Click **AS2 Message and Correlated MDN Status** in the **EDIINT Status Reports** area of the **Group Hub** tab.  
  
   2.  To display the status of the EDI interchange in an AS2 message, right-click an entry in the **AS2 Message and Correlated MDN Status** report, and then click **Interchange/ACK Status**.  
  
       > [!NOTE]
       >  For more information on how EDI status and AS2 status are correlated, see the "Correlating an AS2 Message with its EDI Payload" section of [AS2 Message and Correlated MDN Status Report](../core/as2-message-and-correlated-mdn-status-report.md).  
  
   3.  To display an AS2 message in wire format, right-click an entry in the AS2/MDN Status report, and then click **Message Wire Format**.  
  
   4.  To display an AS2 message in decoded format, right-click an entry in the AS2/MDN Status report, and then click **Message Decoded Format**.  
  
   5.  To display an MDN message, right-click an entry in the AS2/MDN Status report, and then click **Mdn Message**.  
  
## See Also  
 [Monitoring EDI and AS2 Solutions](../core/monitoring-edi-and-as2-solutions.md)   
 [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md)   
 [Enabling EDI and AS2 Status Reports](../core/enabling-edi-and-as2-status-reports.md)   
 [Configuring an EDI and AS2 Status Report](../core/configuring-an-edi-and-as2-status-report.md)