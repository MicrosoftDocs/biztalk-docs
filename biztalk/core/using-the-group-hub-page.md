---
title: "Using the Group Hub Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50693ccc-a3b2-4ad0-9a05-d60dab404a07
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the Group Hub Page
Selecting the **BizTalk Group** node in the BizTalk Server Administration Console, displays the BizTalk Server Group Hub page in the details pane. The BizTalk Server Group Hub page is divided into three sections that provide an overall view of the health of your BizTalk Server system:  
  
-   The **Configuration Overview** section, located in the upper part of the Group Hub page, indicates the overall health of the BizTalk group by displaying the state of the applications, host instances, and adapter handlers configured in this group.  
  
-   The **Work in Progress**  and **Suspended Items** sections are located in the middle of the Group Hub page.  
  
    -   The **Work in Progress** section displays running service instances, dehydrated orchestrations, retrying and idle ports, ready service instances, and scheduled service instances.  
  
    -   The **Suspended Items** section displays the number of suspended service instances, and resumable and non-resumable instances.  
  
-   The **Grouped Suspended Service Instances** section displays suspended service instances grouped by application, service name, error code, and URI.  
  
    > [!NOTE]
    >  The numbers listed on the Group Hub page are approximate counts only. For example, the numbers displayed under **Running service instances** or **Suspended service instances** might not equal the total number of running service instances or suspended service instances because the state of the system could change while the various statistics on the Hub page are being generated.  
  
-   The **Tracked Service Instances** and **Tracked Message Events** sections execute queries on message events and the state of service instances with a maximum match = 50.  
  
    -   **Tracked service instances** query searches for tracked service instances.  
  
    -   **Completed instances** query searches for tracked service instances with state equal to completed.  
  
    -   **Terminated instances** query searches for tracked service instances with state equal to terminated.  
  
    -   **Tracked message events** query searches for tracked message events.  
  
    -   **Transmission failure events** query searches for tracked message events with an event type of transmission failure.  
  
-   The **EDI Status Reports** and **EDIINT Status Reports** sections, located at the bottom of the Group Hub page, displays four reports about EDI interchanges and one about AS2 interchanges: the EDI Interchange and Correlated ACK Status reports, the Batch Status report, the Interchange Aggregation Report, the Transaction Set Aggregation Report, and the AS2 Message and Correlated MDN Status report. For more information about these reports, see [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md).  
  
    > [!NOTE]
    >  The EDI and EDIINT Status Report sections will only be displayed if the EDI/AS2 features are configured for this BizTalk group.  
  
## In This Section  
  
-   [Service Instance States](../core/service-instance-states.md)  
  
-   [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md)  
  
-   [Using the Administration Console Query Tab](../core/using-the-administration-console-query-tab.md)  
  
-   [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)  
  
-   [Health and Activity Tracking](../core/health-and-activity-tracking.md)