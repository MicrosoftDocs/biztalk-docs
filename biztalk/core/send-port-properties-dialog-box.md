---
title: "Send Port Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.sendport.properties"
ms.assetid: 14261d44-dfbe-4074-8b57-6f34a624fd5f
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send Port Properties Dialog Box
Use the **Send Port Properties** window to create new send ports and to configure and view information about the send port you have selected in the details pane.  
  
## General Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Type the name of the port.|  
|**Port type**|Displays the port type. Send ports may be static or dynamic, and they may be one-way or solicit-response. You select the port type when you create the port; if a port has the wrong type, you must re-create the port.|  
|**Transport - Type**|From the drop-down list, select the appropriate transport type, or transport protocol. If the port is a solicit-response port, only transport types that support solicit-response are available in the list.|  
|**Transport - Configure**|After you select the transport type, click **Configure** to display the **Transport Properties** dialog box.|  
|**Transport - URI**|Displays the destination address to which messages sent through the port will go. The URI property applies only to static ports; the destination address for dynamic ports is determined at run time. You enter this property in the **Transport Properties** dialog box.|  
|**Transport - Send handler**|From the drop-down list, select the host instance on which the send adapter is running.|  
|**Send pipeline**|From the drop-down list, select the pipeline that processes the messages sent through this port. After you select the pipeline, you can click the adjacent ellipsis (…) button to display the **Configure Pipeline** dialog box, where you configure pipeline properties. **Note:**  If you have recently deployed a custom pipeline to BizTalk Server, you may need to refresh the **Pipelines** folder for the appropriate BizTalk application in order to select the custom pipeline from the drop-down list.  To refresh the **Pipelines** folder, open the BizTalk Administration console, click to expand the BizTalk group, click to expand **Applications**, click to expand the BizTalk application that the pipeline was deployed to, right-click the **Pipelines** folder and then click the **Refresh** button.|  
|**Receive pipeline**|From the drop-down list, select the pipeline that processes messages received through this port. Responses to messages received through this pipeline will also be sent through this pipeline. After you select the pipeline, you can click the adjacent ellipsis (…) button to display the **Configure Pipeline** dialog box, where you configure pipeline properties.<br /><br /> This property is visible only for Solicit-Response ports. **Note:**  If you have recently deployed a custom pipeline to BizTalk Server, you may need to refresh the **Pipelines** folder for the appropriate BizTalk application in order to select the custom pipeline from the drop-down list.  To refresh the **Pipelines** folder, open the BizTalk Administration console, click to expand the BizTalk group, click to expand **Applications**, click to expand the BizTalk application that the pipeline was deployed to, right-click the **Pipelines** folder and then click the **Refresh** button.|  
|**Description**|Type any text that helps you distinguish this send port from others. The maximum number of characters allowed is 256.|  
  
## Transport Advanced Options Tab  
 The **Transport Advanced Options** tab is visible only for static one way or static solicit-response ports.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Transport Options - Retry count**|Displays the number of times the engine will try to resend if the transmission fails. The default value is 3; the allowed range is 0 to 1000 inclusive.|  
|**Transport Options - Retry interval (minutes)**|Displays the number of minutes the engine waits between retries. The default value is 5; the allowed range is 0 to 525600 inclusive (the number of minutes in 365 days).|  
|**Transport Options - Priority**|Displays the delivery priority of the port. The highest priority is 1, and the lowest is 10. To avoid prioritization of deliveries, set the Priority to the same value on all ports. The Default value is 5.|  
|**Transport Options - Ordered delivery**|Select this check box to specify that messages should be processed in a specified order. Ordered delivery is important for messages that must be processed as a convoy, as specified by a partner business process. The default value of this check box is cleared, meaning the port does not enforce ordered delivery.|  
|**Transport Options - Stop sending subsequent messages on current message failure**|Select this check box if you want the send port instance to be suspended if any of the messages fails to be processed. Clear the check box to suspend only the failed message and enable subsequent messages to continue to be processed.<br /><br /> This check box is available when you select the **Ordered delivery** check box.|  
|**Transport Options - Enable routing for failed messages**|Select this check box if you want enable routing of failed messages. When failed message routing is enabled, failed messages are not suspended but instead are sent to any subscribing routing destination, such as a send port or orchestration.|  
|**Schedule - Enable service window**|Select this check box to configure the port to send only at specified times of the day, then specify the times in the **Start time** and **Stop time** boxes. If the check box is cleared, the send port sends messages at any time. The default value is false (cleared).|  
|**Schedule - Start time**|Specify the time when the port should begin to send messages. This box is available only when the **Enable service window** check box is selected.|  
|**Schedule - Stop time**|Specify the time when the port should cease to send messages. This box is available only when the **Enable service window** check box is selected.|  
  
## Backup Transport Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Backup Transport Options - Type**|From the drop-down list, select the appropriate backup transport type, or transport protocol. If the port is a solicit-response port, only transport types that support solicit-response are available in the list.|  
|**Backup Transport Options - Configure**|After you select the backup transport type, click **Configure** to display the **Transport Properties** dialog box.|  
|**Backup Transport Options - URI**|Displays the destination address to which messages sent through the port will go. The URI property applies only to static ports; the destination address for dynamic ports is determined at run time. You enter this property in the **Transport Properties** dialog box.|  
|**Backup Transport Options - Send handler**|From the drop-down list, select the host instance on which the send adapter is running.|  
|**Backup Transport Options - Retry count**|Displays the number of times the engine will try to resend if the transmission fails. The default value is 3; the allowed range is 0 to 1000 inclusive.|  
|**Backup Transport Options - Retry interval**|Displays the number of minutes the engine waits between retries. The default value is 5; the allowed range is 0 to 525600 inclusive (the number of minutes in 365 days).|  
|**Schedule - Enable service window**|Select this check box to configure the port to send only at specified times of the day, then specify the times in the **Start time** and **Stop time** boxes. If the check box is cleared, the send port sends messages at any time. The default value is false (cleared).|  
|**Schedule - Start time**|Specify the time when the port should begin to send messages. This box is available only when the **Enable service window** check box is selected.|  
|**Schedule - Stop time**|Specify the time when the port should cease to send messages. This box is available only when the **Enable service window** check box is selected.|  
  
## Inbound Maps Tab  
 The **Inbound Maps** tab is visible only for solicit-response pipelines.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Remove**|Click to remove the selected map from the project.|  
|**Inbound maps - Source Document**|From the drop-down list, select the source document for the inbound map. A send port may have more than one map, but each map should have a unique source document.|  
|**Inbound maps - Map**|From the drop-down list, select the map to associate with the source and target documents.|  
|**Inbound maps - Target Document**|From the drop-down list, select the target document for the inbound map.|  
  
## Outbound Maps Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Remove**|Click to remove the selected map.|  
|**Outbound maps - Source Document**|From the drop-down list, select the source document for the outbound map.|  
|**Outbound maps - Map**|From the drop-down list, select the map to associate with the source and target documents.|  
|**Outbound maps - Target Document**|From the drop-down list, select the target document for the outbound map.|  
  
## Filters Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Delete**|Click to delete the selected filter expression.|  
|**Move Up**|Click to move the selected property ahead in the filter expression sequence.|  
|**Move Down**|Click to move the selected property down in the filter expression sequence.|  
|**Property**|Select a property reference to be used on messages transiting through the port.|  
|**Operator**|Type or select the operator for the expression.|  
|**Value**|Type the value to validate against the property.|  
|**Group by**|Select **And** or **Or** to indicate the relationship between two filter expressions.|  
  
## Certificate Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Encryption certificate – Common Name**|Displays the common name of the selected certificate.|  
|**Encryption certificate - Thumbprint**|Displays the encryption certificate thumbprint used to retrieve the public key certificate from the Other People certificate store. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.|  
|**Remove certificate**|Click to remove the displayed certificate.|  
|**Browse**|Click to display the **Select Certificate** dialog box, where you can select the encryption certificate to use for this port.|  
  
## Tracking Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Track Message Bodies - Request message before port processing**|Select this check box to enable you to save and track message content before the message is received.|  
|**Track Message Bodies - Request message after port processing**|Select this check box to enable you to save and track message content after the message is received.|  
|**Track Message Bodies - Response message before port processing**|Select this check box to enable you to save and track message content before the message is sent. This check box is available only for solicit-response send ports.|  
|**Track Message Bodies - Response message after port processing**|Select this check box to enable you to save and track message content after the message is sent. This check box is available only for solicit-response send ports.|  
|**Track Message Properties - Request message before port processing**|Select this check box to track the promoted properties of an inbound message.|  
|**Track Message Properties - Request message before port processing**|Select this check box if you want to track the promoted properties of an outbound message.|  
|**Track Message Properties - Response message before port processing**|Select this check box to save and track message properties before the message is sent. This check box is available only for solicit-response send ports.|  
|**Track Message Properties - Response message after port processing**|Select this check box to save and track properties after the message is sent. This check box is available only for solicit-response send ports.|  
  
## See Also  
 [How to Enlist a Send Port or Send Port Group](../core/how-to-enlist-a-send-port-or-send-port-group.md)   
 [Managing Send Ports and Send Port Groups](../core/managing-send-ports-and-send-port-groups.md)   
 [How to Start a Send Port or Send Port Group](../core/how-to-start-a-send-port-or-send-port-group.md)   
 [How to Stop a Send Port or Send Port Group](../core/how-to-stop-a-send-port-or-send-port-group.md)   
 [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)