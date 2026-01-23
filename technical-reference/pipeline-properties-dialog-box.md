---
description: "Learn more about: Pipeline Properties Dialog Box"
title: Pipeline Properties Dialog Box
TOCTitle: Pipeline Properties Dialog Box
ms:assetid: 595e8ade-ce12-4bbb-b9b0-ebeea7bb14a6
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560297(v=BTS.80)
ms:contentKeyID: 51528234
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.pipeline.properties
---

# Pipeline Properties Dialog Box

You can use the **Pipeline Properties** window to view information on all the pipelines that are deployed in the application, as well as default pipelines that are deployed in every BizTalk installation. You can also configure message tracking options for pipelines. Pipeline properties are configured in Microsoft Visual Studio. The **Description** box is an exception; you can edit it in the **Pipeline Properties** window.

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
<td>Displays the full name of the pipeline.</td>
</tr>
<tr class="even">
<td><strong>Assembly</strong></td>
<td>Displays the fully qualified name (name, version, culture, public key token) of the assembly that contains the pipeline.</td>
</tr>
<tr class="odd">
<td><strong>Type</strong></td>
<td>Indicates whether the pipeline is a send or receive pipeline.</td>
</tr>
<tr class="even">
<td><strong>Description</strong></td>
<td>Type any text that helps you distinguish this pipeline from others. The maximum number of characters allowed is 256.</td>
</tr>
</tbody>
</table>

## Tracking Tab

Pipelines and orchestrations use virtually the same tracking options. You can track promoted message properties from pipelines just as you can from orchestrations.

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
<td><strong>Track Events - Port start and end events</strong></td>
<td>Select this check box to track only when an instance starts and ends. Details included are item name, assembly, and other metadata.</td>
</tr>
<tr class="even">
<td><strong>Track Events - Message send and receive events</strong></td>
<td>Select this check box to track message send and receive events. This check box is available only if <strong>Port start and end events</strong> is selected.</td>
</tr>
<tr class="odd">
<td><strong>Track Message Bodies - Messages before pipeline processing</strong></td>
<td>Select this check box to save and track the actual message content as received by the pipeline, along with the shortcut, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the raw message as submitted to the pipeline by the transport component. Depending on the application, the message might be encrypted, signed, or encoded. When using a BizTalk map, if this is a receive pipeline, tracking takes place after the inbound map is processed.<br />
<br />
This check box is available only if <strong>Message send and receive events</strong> is selected.</td>
</tr>
<tr class="even">
<td><strong>Track Message Bodies - Messages after pipeline processing</strong></td>
<td>Select this check box to save and track the actual message content as sent by the pipeline, along with the shortcut, which holds metadata such as URLs and promoted properties. If this is a receive pipeline, the message body is the processed message to be submitted to the MessageBox database, which may be XML depending on your application. When using a BizTalk map, if this is a send pipeline, tracking takes place before the outbound map is processed.<br />
<br />
This check box is available only if <strong>Message send and receive events</strong> is selected.</td>
</tr>
</tbody>
</table>

## See Also

[About Pipelines, Stages, and Components](https://msdn.microsoft.com/library/aa577959\(v=bts.80\))  
[How to Create a New Pipeline](https://msdn.microsoft.com/library/aa578387\(v=bts.80\))  
[Investigating Orchestration, Port, and Message Failures](https://msdn.microsoft.com/library/aa560126\(v=bts.80\))  
[Receive Pipelines](https://msdn.microsoft.com/library/aa561803\(v=bts.80\))  
[Send Pipelines](https://msdn.microsoft.com/library/aa547976\(v=bts.80\))
