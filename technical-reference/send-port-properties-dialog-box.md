---
description: "Learn more about: Send Port Properties Dialog Box"
title: Send Port Properties Dialog Box
TOCTitle: Send Port Properties Dialog Box
ms:assetid: 14261d44-dfbe-4074-8b57-6f34a624fd5f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547640(v=BTS.80)
ms:contentKeyID: 51526367
ms.date: 12/23/2019
ms.custom: biztalk-2020
mtps_version: v=BTS.80
ms.topic: ui-reference
f1_keywords:
- bts10.admin.sendport.properties
---

# Send Port Properties Dialog Box

Use the **Send Port Properties** window to create new send ports and to configure and view information about the send port you have selected in the details pane.

## General Tab

The following table lists the UIElements in the **General** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Name</strong></td>
<td>Type the name of the port.</td>
</tr>
<tr class="even">
<td><strong>Port type</strong></td>
<td>Displays the port type. Send ports may be static or dynamic, and they may be one-way or solicit-response. You select the port type when you create the port; if a port has the wrong type, you must re-create the port.</td>
</tr>
<tr class="odd">
<td><strong>Transport - Type</strong></td>
<td>From the drop-down list, select the appropriate transport type, or transport protocol. If the port is a solicit-response port, only transport types that support solicit-response are available in the list.</td>
</tr>
<tr class="even">
<td><strong>Transport - Configure</strong></td>
<td>After you select the transport type, click <strong>Configure</strong> to display the <strong>Transport Properties</strong> dialog box.</td>
</tr>
<tr class="odd">
<td><strong>Transport - URI</strong></td>
<td>Displays the destination address to which messages sent through the port will go. The URI property applies only to static ports; the destination address for dynamic ports is determined at run time. You enter this property in the <strong>Transport Properties</strong> dialog box.</td>
</tr>
<tr class="even">
<td><strong>Transport - Send handler</strong></td>
<td>From the drop-down list, select the host instance on which the send adapter is running.</td>
</tr>
<tr class="odd">
<td><strong>Send pipeline</strong></td>
<td>From the drop-down list, select the pipeline that processes the messages sent through this port. After you select the pipeline, you can click the adjacent ellipsis (…) button to display the <strong>Configure Pipeline</strong> dialog box, where you configure pipeline properties. <strong>Note:</strong> If you have recently deployed a custom pipeline to BizTalk Server, you may need to refresh the <strong>Pipelines</strong> folder for the appropriate BizTalk application in order to select the custom pipeline from the drop-down list. To refresh the <strong>Pipelines</strong> folder, open the BizTalk Administration console, click to expand the BizTalk group, click to expand <strong>Applications</strong>, click to expand the BizTalk application that the pipeline was deployed to, right-click the <strong>Pipelines</strong> folder and then click the <strong>Refresh</strong> button.</td>
</tr>
<tr class="even">
<td><strong>Receive pipeline</strong></td>
<td>From the drop-down list, select the pipeline that processes messages received through this port. Responses to messages received through this pipeline will also be sent through this pipeline. After you select the pipeline, you can click the adjacent ellipsis (…) button to display the <strong>Configure Pipeline</strong> dialog box, where you configure pipeline properties.<br />
<br />
This property is visible only for Solicit-Response ports. <strong>Note:</strong> If you have recently deployed a custom pipeline to BizTalk Server, you may need to refresh the <strong>Pipelines</strong> folder for the appropriate BizTalk application in order to select the custom pipeline from the drop-down list. To refresh the <strong>Pipelines</strong> folder, open the BizTalk Administration console, click to expand the BizTalk group, click to expand <strong>Applications</strong>, click to expand the BizTalk application that the pipeline was deployed to, right-click the <strong>Pipelines</strong> folder and then click the <strong>Refresh</strong> button.</td>
</tr>
<tr class="odd">
<td><strong>Description</strong></td>
<td>Type any text that helps you distinguish this send port from others. The maximum number of characters allowed is 256.</td>
</tr>
</tbody>
</table>


## Transport Advanced Options Tab

Only some of the following properties in the **Transport Advanced Options** tab are available for dynamic send ports.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Transport Options - Retry count</strong></td>
<td>Displays the number of times the engine will try to resend if the transmission fails. The default value is 3; the allowed range is 0 to 1000 inclusive.</td>
</tr>
<tr class="even">
<td><strong>Transport Options - Retry interval (minutes)</strong></td>
<td>Displays the number of minutes the engine waits between retries. The default value is 5; the allowed range is 0 to 525600 inclusive (the number of minutes in 365 days).</td>
</tr>
<tr class="odd">
<td><strong>Transport Options - Priority</strong></td>
<td>Displays the delivery priority of the port. The highest priority is 1, and the lowest is 10. To avoid prioritization of deliveries, set the Priority to the same value on all ports. The Default value is 5.</td>
</tr>
<tr class="even">
<td><strong>Transport Options - Ordered delivery</strong></td>
<td>Select this check box to specify that messages should be processed in a specified order. Ordered delivery is important for messages that must be processed as a convoy, as specified by a partner business process. The default value of this check box is cleared, meaning the port does not enforce ordered delivery.</td>
</tr>
<tr class="odd">
<td><strong>Transport Options - Stop sending subsequent messages on current message failure</strong></td>
<td>Select this check box if you want the send port instance to be suspended if any of the messages fails to be processed. Clear the check box to suspend only the failed message and enable subsequent messages to continue to be processed.<br />
This check box is available when you select the <strong>Ordered delivery</strong> check box.</td>
</tr>
<tr class="even">
<td><strong>Transport Options - Enforce order across outbound locations</strong></td>
<td>This property is visible only for Dynamic send ports. <br />
Select this check box if you want messages to be ordered across all outbound locations for a given transport type. The default value of this check box is cleared, meaning the port does not enforce ordered delivery of messages across different outbound locations, even for the same transport type.<br />
This check box is available when you select the <strong>Ordered delivery</strong> check box.</td>
</tr>
<tr class="odd">
<td><strong>Transport Options - Enable routing for failed messages</strong></td>
<td>Select this check box if you want enable routing of failed messages. When failed message routing is enabled, failed messages are not suspended but instead are sent to any subscribing routing destination, such as a send port or orchestration.</td>
</tr>
<tr class="even">
<td><strong>Schedule - Enable service window</strong></td>
<td>Select this check box to configure the port to send only at specified times of the day, then specify the times in the <strong>Start time</strong> and <strong>Stop time</strong> boxes. If the check box is cleared, the send port sends messages at any time. The default value is false (cleared).</td>
</tr>
<tr class="odd">
<td><strong>Schedule - Start time</strong></td>
<td>Specify the time when the port should begin to send messages. This box is available only when the <strong>Enable service window</strong> check box is selected.</td>
</tr>
<tr class="even">
<td><strong>Schedule - Stop time</strong></td>
<td>Specify the time when the port should cease to send messages. This box is available only when the <strong>Enable service window</strong> check box is selected.</td>
</tr>
</tbody>
</table>


## Backup Transport Tab

The following table lists the UIElements in the **Backup Transport** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Backup Transport Options - Type</strong></td>
<td>From the drop-down list, select the appropriate backup transport type, or transport protocol. If the port is a solicit-response port, only transport types that support solicit-response are available in the list.</td>
</tr>
<tr class="even">
<td><strong>Backup Transport Options - Configure</strong></td>
<td>After you select the backup transport type, click <strong>Configure</strong> to display the <strong>Transport Properties</strong> dialog box.</td>
</tr>
<tr class="odd">
<td><strong>Backup Transport Options - URI</strong></td>
<td>Displays the destination address to which messages sent through the port will go. The URI property applies only to static ports; the destination address for dynamic ports is determined at run time. You enter this property in the <strong>Transport Properties</strong> dialog box.</td>
</tr>
<tr class="even">
<td><strong>Backup Transport Options - Send handler</strong></td>
<td>From the drop-down list, select the host instance on which the send adapter is running.</td>
</tr>
<tr class="odd">
<td><strong>Backup Transport Options - Retry count</strong></td>
<td>Displays the number of times the engine will try to resend if the transmission fails. The default value is 3; the allowed range is 0 to 1000 inclusive.</td>
</tr>
<tr class="even">
<td><strong>Backup Transport Options - Retry interval</strong></td>
<td>Displays the number of minutes the engine waits between retries. The default value is 5; the allowed range is 0 to 525600 inclusive (the number of minutes in 365 days).</td>
</tr>
<tr class="odd">
<td><strong>Schedule - Enable service window</strong></td>
<td>Select this check box to configure the port to send only at specified times of the day, then specify the times in the <strong>Start time</strong> and <strong>Stop time</strong> boxes. If the check box is cleared, the send port sends messages at any time. The default value is false (cleared).</td>
</tr>
<tr class="even">
<td><strong>Schedule - Start time</strong></td>
<td>Specify the time when the port should begin to send messages. This box is available only when the <strong>Enable service window</strong> check box is selected.</td>
</tr>
<tr class="odd">
<td><strong>Schedule - Stop time</strong></td>
<td>Specify the time when the port should cease to send messages. This box is available only when the <strong>Enable service window</strong> check box is selected.</td>
</tr>
</tbody>
</table>


## Inbound Maps Tab

The **Inbound Maps** tab is visible only for solicit-response pipelines.

The following table lists the UIElements in the **Inbound Maps** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Click to remove the selected map from the project.</td>
</tr>
<tr class="even">
<td><strong>Inbound maps - Source Document</strong></td>
<td>From the drop-down list, select the source document for the inbound map. A send port may have more than one map, but each map should have a unique source document.</td>
</tr>
<tr class="odd">
<td><strong>Inbound maps - Map</strong></td>
<td>From the drop-down list, select the map to associate with the source and target documents.</td>
</tr>
<tr class="even">
<td><strong>Inbound maps - Target Document</strong></td>
<td>From the drop-down list, select the target document for the inbound map.</td>
</tr>
</tbody>
</table>

## Outbound Maps Tab

The following table lists the UIElements in the **Outbound Maps** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Click to remove the selected map.</td>
</tr>
<tr class="even">
<td><strong>Outbound maps - Source Document</strong></td>
<td>From the drop-down list, select the source document for the outbound map.</td>
</tr>
<tr class="odd">
<td><strong>Outbound maps - Map</strong></td>
<td>From the drop-down list, select the map to associate with the source and target documents.</td>
</tr>
<tr class="even">
<td><strong>Outbound maps - Target Document</strong></td>
<td>From the drop-down list, select the target document for the outbound map.</td>
</tr>
</tbody>
</table>

## Filters Tab

The following table lists the UIElements in the **Filters** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Delete</strong></td>
<td>Click to delete the selected filter expression.</td>
</tr>
<tr class="even">
<td><strong>Move Up</strong></td>
<td>Click to move the selected property ahead in the filter expression sequence.</td>
</tr>
<tr class="odd">
<td><strong>Move Down</strong></td>
<td>Click to move the selected property down in the filter expression sequence.</td>
</tr>
<tr class="even">
<td><strong>Property</strong></td>
<td>Select a property reference to be used on messages transiting through the port.</td>
</tr>
<tr class="odd">
<td><strong>Operator</strong></td>
<td>Type or select the operator for the expression.</td>
</tr>
<tr class="even">
<td><strong>Value</strong></td>
<td>Type the value to validate against the property.</td>
</tr>
<tr class="odd">
<td><strong>Group by</strong></td>
<td>Select <strong>And</strong> or <strong>Or</strong> to indicate the relationship between two filter expressions.</td>
</tr>
</tbody>
</table>

## Certificate Tab

The following table lists the UIElements in the **Certificate** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Encryption certificate – Common Name</strong></td>
<td>Displays the common name of the selected certificate.</td>
</tr>
<tr class="even">
<td><strong>Encryption certificate - Thumbprint</strong></td>
<td>Displays the encryption certificate thumbprint used to retrieve the public key certificate from the Other People certificate store. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.</td>
</tr>
<tr class="odd">
<td><strong>Remove certificate</strong></td>
<td>Click to remove the displayed certificate.</td>
</tr>
<tr class="even">
<td><strong>Browse</strong></td>
<td>Click to display the <strong>Select Certificate</strong> dialog box, where you can select the encryption certificate to use for this port.</td>
</tr>
</tbody>
</table>

## Tracking Tab

The following table lists the UIElements in the **Tracking** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Track Message Bodies - Request message before port processing</strong></td>
<td>Select this check box to enable you to save and track message content before the message is received.</td>
</tr>
<tr class="even">
<td><strong>Track Message Bodies - Request message after port processing</strong></td>
<td>Select this check box to enable you to save and track message content after the message is received.</td>
</tr>
<tr class="odd">
<td><strong>Track Message Bodies - Response message before port processing</strong></td>
<td>Select this check box to enable you to save and track message content before the message is sent. This check box is available only for solicit-response send ports.</td>
</tr>
<tr class="even">
<td><strong>Track Message Bodies - Response message after port processing</strong></td>
<td>Select this check box to enable you to save and track message content after the message is sent. This check box is available only for solicit-response send ports.</td>
</tr>
<tr class="odd">
<td><strong>Track Message Properties - Request message before port processing</strong></td>
<td>Select this check box to track the promoted properties of an inbound message.</td>
</tr>
<tr class="even">
<td><strong>Track Message Properties - Request message before port processing</strong></td>
<td>Select this check box if you want to track the promoted properties of an outbound message.</td>
</tr>
<tr class="odd">
<td><strong>Track Message Properties - Response message before port processing</strong></td>
<td>Select this check box to save and track message properties before the message is sent. This check box is available only for solicit-response send ports.</td>
</tr>
<tr class="even">
<td><strong>Track Message Properties - Response message after port processing</strong></td>
<td>Select this check box to save and track properties after the message is sent. This check box is available only for solicit-response send ports.</td>
</tr>
</tbody>
</table>

## See Also

[How to Enlist a Send Port or Send Port Group](https://msdn.microsoft.com/library/aa578592\(v=bts.80\))  
[Managing Send Ports and Send Port Groups](https://msdn.microsoft.com/library/aa561407\(v=bts.80\))  
[How to Start a Send Port or Send Port Group](https://msdn.microsoft.com/library/aa561872\(v=bts.80\))  
[How to Stop a Send Port or Send Port Group](https://msdn.microsoft.com/library/aa577932\(v=bts.80\))  
[How to Unenlist a Send Port or Send Port Group](https://msdn.microsoft.com/library/aa559480\(v=bts.80\))  
[Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\))
