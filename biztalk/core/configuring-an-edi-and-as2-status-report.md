---
title: "Configure an EDI and AS2 Status Report | Microsoft Docs"
description: Create the EDI or AS2 status report query expression, and select the data you want displayed in the report for in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6490864d-f1e6-4932-aefb-c332a595aad7
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure an EDI and AS2 Status Report
After you have enabled EDI or AS2 status reports, you display the status report you want from the **EDI Status Reports** or **EDIINT Status Reports** section of the **Group Hub** tab of the **Group Overview** page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. When you display a status report, you will see a default set of data. You can configure the following aspects of the status reports:  
  
- The query expression that is run to determine the range of data that status is reported for, for example, the date range, the direction of the data (receive or send), or the status value (Accepted, Rejected, All, etc.)  
  
- The type of data displayed in the status report pane, as determined by the data columns in the report.  
  
  > [!NOTE]
  >  Whenever status reporting is enabled, all status will be saved in storage. By customizing the query expression or status columns, you are defining which saved data is displayed.  
  
  Five different EDI and AS2 status reports are available (see [Types of EDI and AS2 Status Reports](../core/types-of-edi-and-as2-status-reports.md)). The way that you configure each report is the same, even though the data for each report is different.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
## Configure the status report query expression  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **BizTalk Group** node to see the **Group Overview** pane.  
  
2. At the bottom of the **Group Hub** tab in the **Group Overview** pane, click the status report that you want to configure, such as **EDI Interchange and Correlated ACK Status**.  
  
3. In the **Query Expression** area of the status report pane, verify that all filter criteria that you want to define for the query are present. If not, click the down arrow in the empty row in the **Field Name** column at the bottom of the query expression, and select any filter criteria that you want to add to the query expression. You can delete a filter criteria row by selecting the row and clicking the **Delete** button on the keyboard.  
  
4. Verify that the values for the filter expressions are as desired. If not, click the down arrow for the **Operator** column to select a query operation, and enter the appropriate value in the **Value** column.  
  
   > [!NOTE]
   >  The operators and values available for filter criteria in the query expressions are described in [Types of EDI and AS2 Status Reports](../core/types-of-edi-and-as2-status-reports.md) and the **EDI-AS2 Status Reports UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
5. To run the query, displaying the status report according to the filter criteria, click **Run Query**.  
  
6. To save a query expression as a .btq file, click **Save As**, specify the folder and enter a filename, and then click **Save**.  
  
7. To open a saved .btq file, click **Open Query**.  
  
## Configure the type of data displayed in the status report pane  
  
1.  Right-click the status results area of the status report pane, and then click **Add/Remove Columns**.  
  
2.  To add a status category to the displayed columns list, click a column in the **Available columns** list, and then click **Add**.  
  
3.  To remove a status category from the displayed columns list, click a column in the **Displayed columns** list, and then click **Remove**.  
  
## See Also  
 [Monitoring EDI and AS2 Solutions](../core/monitoring-edi-and-as2-solutions.md)   
 [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md)   
 [Enabling EDI and AS2 Status Reports](../core/enabling-edi-and-as2-status-reports.md)   
 [Displaying an EDI or AS2 Status Report](../core/displaying-an-edi-or-as2-status-report.md)