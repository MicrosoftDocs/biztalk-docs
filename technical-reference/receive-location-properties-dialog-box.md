---
title: Receive Location Properties Dialog Box
TOCTitle: Receive Location Properties Dialog Box
ms:assetid: a51afe52-a9a5-40c0-b3ca-51abdf6d7a3f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577877(v=BTS.80)
ms:contentKeyID: 51530271
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.receivelocation.properties
---

# Receive Location Properties Dialog Box

 

Use the **Receive Location Properties** window to configure receive locations and associate them with receive ports and pipelines.

## General Tab

Use the **General** tab to associate the receive location with the receive handler of the selected host.

## UIElement List

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
<td>Type the name of the receive location.</td>
</tr>
<tr class="even">
<td><strong>Receive port</strong></td>
<td>Displays the name of the parent receive port associated with this receive location. You select the receive port in the <strong>Select a Receive Port</strong> dialog box when you create the receive location.</td>
</tr>
<tr class="odd">
<td><strong>Transport - Type</strong></td>
<td>From the drop-down list, select the transport type, or transport protocol. If you change the transport type, you must change the URI.</td>
</tr>
<tr class="even">
<td><strong>Transport - Configure</strong></td>
<td>After you select the transport type, click <strong>Configure</strong> to display the <strong>Transport Properties</strong> dialog box and configure adapter properties for the receive location.</td>
</tr>
<tr class="odd">
<td><strong>Transport - URI</strong></td>
<td>Displays the destination address to which messages sent through the port will go. You enter this property in the <strong>Transport Properties</strong> dialog box.</td>
</tr>
<tr class="even">
<td><strong>Transport - Receive handler</strong></td>
<td>From the drop-down list, select the instance of the BizTalk Server host on which the receive location is running.</td>
</tr>
<tr class="odd">
<td><strong>Receive pipeline</strong></td>
<td>From the drop-down list, select the receive pipeline to use to receive messages at this receive location. <strong>Note:</strong> If you have recently deployed a custom pipeline to BizTalk Server, you may need to refresh the <strong>Pipelines</strong> folder for the appropriate BizTalk application in order to select the custom pipeline from the drop-down list. To refresh the <strong>Pipelines</strong> folder, open the BizTalk Administration console, click to expand the BizTalk group, click to expand <strong>Applications</strong>, click to expand the BizTalk application that the pipeline was deployed to, right-click the <strong>Pipelines</strong> folder and then click the <strong>Refresh</strong> button.</td>
</tr>
<tr class="even">
<td><strong>Send pipeline</strong></td>
<td>From the drop-down list, select the send pipeline to use to send responses from this receive location. This list is available only for a receive location associated with a request-response receive port. <strong>Note:</strong> If you have recently deployed a custom pipeline to BizTalk Server, you may need to refresh the <strong>Pipelines</strong> folder for the appropriate BizTalk application in order to select the custom pipeline from the drop-down list. To refresh the <strong>Pipelines</strong> folder, open the BizTalk Administration console, click to expand the BizTalk group, click to expand <strong>Applications</strong>, click to expand the BizTalk application that the pipeline was deployed to, right-click the <strong>Pipelines</strong> folder and then click the <strong>Refresh</strong> button.</td>
</tr>
<tr class="odd">
<td><strong>Make this the primary location</strong></td>
<td>Select this check box if you have more than one receive location for a receive port and you want this receive location to represent the receive port when the port needs to be passed to another entity, such as a business partner, that needs to send messages to your organization. The first receive location created is automatically selected as the primary receive location. This property remains selected and unavailable until you designate a different receive location as the primary.</td>
</tr>
<tr class="even">
<td><strong>Description</strong></td>
<td>Type a description of the receive location.</td>
</tr>
</tbody>
</table>


## Schedule Tab

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Start date</strong></td>
<td>From the pull-down calendar, select the date on which the receive location starts processing messages. To change the year, click the displayed year.</td>
</tr>
<tr class="even">
<td><strong>Stop date</strong></td>
<td>From the pull-down calendar, select the date on which the receive location stops processing messages. This property is optional. If you do not specify a stop date, the receive location remains active until it is disabled.</td>
</tr>
<tr class="odd">
<td><strong>Service Window - Enable service window</strong></td>
<td>Select this check box to configure the receive location to receive messages only at specified times of the day, then specify the times in the <strong>Start time and Stop time</strong> boxes. If the check box is cleared, the receive location receives messages at any time. The default value is false (cleared).</td>
</tr>
<tr class="even">
<td><strong>Service Window - Start time</strong></td>
<td>Specify the time when the receive location should begin to receive messages. This box is available only when the <strong>Enable service window</strong> check box is selected.</td>
</tr>
<tr class="odd">
<td><strong>Service Window - Stop time</strong></td>
<td>Specify the time when the receive location should cease to receive messages. This box is available only when the <strong>Enable service window</strong> check box is selected.</td>
</tr>
</tbody>
</table>


## Certificate Tab

The **Certificate** tab appears only for request-response receive locations.

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Encryption certificate - Description</strong></td>
<td>Displays a description of the selected encryption certificate.</td>
</tr>
<tr class="even">
<td><strong>Encryption certificate - Thumbprint</strong></td>
<td>Displays the thumbprint of the public key certificate used to encrypt outbound messages. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.</td>
</tr>
<tr class="odd">
<td><strong>Encryption certificate - Remove certificate</strong></td>
<td>Click to remove the selected certificate.</td>
</tr>
<tr class="even">
<td><strong>Encryption certificate - Browse</strong></td>
<td>Click to display the <strong>Select Certificate</strong> dialog box, where you select the encryption certificate from the Local Machine or Other People certificate store to use for this receive location.</td>
</tr>
</tbody>
</table>


## See Also

[Receive Locations](https://msdn.microsoft.com/library/aa578407\(v=bts.80\))  
[How to Configure a Windows SharePoint Services Receive Location](https://msdn.microsoft.com/library/aa560390\(v=bts.80\))  
[How to Configure Scheduling for a Receive Location](https://msdn.microsoft.com/library/aa559260\(v=bts.80\))  
[How to Enable a Receive Location](https://msdn.microsoft.com/library/aa561716\(v=bts.80\))  
[Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\))

