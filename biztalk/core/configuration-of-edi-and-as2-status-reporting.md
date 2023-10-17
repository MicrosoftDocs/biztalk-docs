---
description: "Learn more about: Configuration of EDI and AS2 Status Reporting"
title: "Configuration of EDI and AS2 Status Reporting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c7fa76d-0d03-4b74-9a3a-60f4bd0534ff
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration of EDI and AS2 Status Reporting
This topic describes the enabling of EDI and AS2 status reporting, and the configuration of status report filters and display columns for EDI, batching, and AS2 status reports.  
  
## Enabling Status Reporting  
 EDI status reporting will only be available on a server if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with the EDI and BAM subsystems is installed on that server. EDI/AS2 status reporting cannot be enabled if the BAM infrastructure is not installed. The server must also be a member of the EDI Processing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group so that it has access to the EDI status report data store.  
  
 EDI message entries will be entered for a party's interchanges in the status report UI if the **Turn ON reporting** property is selected in the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box. If the party sending or being sent interchanges is not determined, EDI message entries will be entered for those interchanges only if the **Activate EDI reporting** property is selected in the fallback agreement for both X12 and EDIFACT. This applies to the EDI Interchange and Correlated ACK Status report. The Batch Status report is enabled only if an agreement has been determined and the **Turn ON reporting** property is selected in **General Properties** page of the **General** tab in the **Agreement Properties** dialog box.  
  
 Transaction sets will be stored in the tracking database if the **Store message payload for reporting** property is selected in **General Properties** page of the **General** tab in the **Agreement Properties** dialog box or **Store transaction set/payload for reporting** property is set in the fallback agreement properties. The Transaction Set Details and Message Content status reports will only be available if this property is selected.  
  
 AS2 message entries will be entered in the status report UI if the **Turn ON reporting** property is selected in the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box. To store AS2 message or MDNs in the non-repudiation database, you must select the appropriate property in the **Sender Non-repudiation** or **Receiver non-repudiation** pages of the one-way AS2 agreement tab in the **Agreement Properties** dialog box. These properties enable the AS2 Message and Correlated MDN Status report.  
  
 The Reliable Messaging Status report will be available if the **Resend AS2 message if MDN not received** property is enabled on **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box.  
  
 For more information about enabling status reporting, see [Enabling EDI and AS2 Status Reports](../core/enabling-edi-and-as2-status-reports.md).  
  
## Status Report Filters and Display Columns  
 EDI and AS2 status reporting enables you to customize the range of the data that is saved for the status report. You do so in the **Group Hub** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. Once you have displayed the status report pane for any of the status reports, you can select the range of data that you want to see in the report. You do so by selecting the filter values to include in the status report query expression.  
  
 You can also customize the type of data that is displayed in the status report.  
  
> [!NOTE]
>  Whenever status reporting is enabled, all status will be saved in storage. By customizing the query expression or status columns, you are defining which saved data is displayed.  
  
 For more information, see [Configuring an EDI and AS2 Status Report](../core/configuring-an-edi-and-as2-status-report.md).  
  
## See Also  
 [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md)   
 [EDI Interchange and Correlated ACK Status Report](../core/edi-interchange-and-correlated-ack-status-report.md)   
 [Batch Status Report](../core/batch-status-report.md)   
 [Interchange Aggregation Report](../core/interchange-aggregation-report.md)   
 [Transaction Set Aggregation Report](../core/transaction-set-aggregation-report.md)   
 [AS2 Message and Correlated MDN Status Report](../core/as2-message-and-correlated-mdn-status-report.md)
