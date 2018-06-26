---
title: "How to Search for Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, viewing"
  - "messages, searching"
  - "Query tab [Administration Console], searching"
  - "Query tab [Administration Console], messages"
ms.assetid: c751d23f-913a-4325-81da-a36d61c07e8b
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Search for Messages
You can use the **Query** tab in the BizTalk Server Administration Console to search for a specific class of messages.  

## Prerequisites  
 To perform this procedure, you must be logged on as a member of the BizTalk Server Operators group.  

### To search for messages  

1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], and then click the BizTalk group.  

3. In the details pane, click the **New Query** tab.  

4. In the **Query Expression** group, in the **Value** column, select **Messages** from the drop-down list box.  

5. In the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\***), select one or more of the following:  


   |          Item           |                                                                                                                                                                Description                                                                                                                                                                |
   |-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |    **Creation Time**    |                                                                                                                                         Find messages created before or after the specified date.                                                                                                                                         |
   |    **Error Adapter**    |                                                                                                   You can group or filter messages by adapter type: FILE, FTP, HTTP, MQSeries, MSMQ, POP3, SMTP, SOAP, or Windows SharePoint Services.                                                                                                    |
   |     **Error Code**      |                                                                                                                                              You can group or filter messages by error code.                                                                                                                                              |
   |  **Error Description**  |                                                                                                                                          You can group or filter messages by error description.                                                                                                                                           |
   |      **Host Name**      |                                                                                                                                              You can group or filter messages by host name.                                                                                                                                               |
   |   **Instance Status**   | The status of the service instance referencing the message. You can search for all of the following types of instances: all running instances, all suspended instances, active instances, dehydrated instances, ready-to-run instances, scheduled instances, suspended but not resumable instances, or suspended and resumable instances. |
   |   **Maximum Matches**   |                                                                                                                                                     The number of matches to display.                                                                                                                                                     |
   |     **Message ID**      |                                                                                                                                              You can group or filter messages by message ID.                                                                                                                                              |
   |   **Message Status**    |                                                 You can search for messages with consumed, in process, suspended, suspended but not resumable, suspended and resumable, queued, queued but awaiting processing, queued but scheduled for later delivery, and queued but waiting to retry.                                                 |
   |    **Message Type**     |                                                                                                                                             You can group or filter messages by message type.                                                                                                                                             |
   |    **Service Class**    |                                                                                                    You can search for isolated adapters; messaging; messaging, and isolated adapters; MSMQT; Orchestration; or Routing Failure Report.                                                                                                    |
   | **Service Instance ID** |                                                                                                                                         You can group or filter messages by service instance ID.                                                                                                                                          |
   |    **Service Name**     |                                                                                                                                             You can group or filter messages by service name.                                                                                                                                             |
   |   **Service Type ID**   |                                                                                                                                           You can group or filter messages by service type ID.                                                                                                                                            |
   |         **URI**         |                                                                                                                                                 You can group or filter messages by URI.                                                                                                                                                  |


6. Complete the **Value** column as appropriate for the selection you made in the **Field Name** column.  

7. Continue adding additional lines to the query as appropriate, by completing the **Field Name**, **Operator**, and **Values** columns, and then click **Run Query**.  

## See Also  
 [Using the Administration Console Query Tab](../core/using-the-administration-console-query-tab.md)