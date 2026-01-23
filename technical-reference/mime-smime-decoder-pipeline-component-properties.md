---
description: "Learn more about: MIME-SMIME Decoder Pipeline Component Properties"
title: MIME-SMIME Decoder Pipeline Component Properties
TOCTitle: MIME-SMIME Decoder Pipeline Component Properties
ms:assetid: b272610f-f6ad-4466-9931-b96595ed4cc1
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578167(v=BTS.80)
ms:contentKeyID: 51530578
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: ui-reference
f1_keywords:
- Microsoft.BizTalk.Component.MIME_SMIME_Decoder
---

# MIME-SMIME Decoder Pipeline Component Properties

 

Use the MIME/SMIME decoder pipeline component to provide MIME decoding functionality to messages.

The MIME/SMIME decoder pipeline component is intended for use in the Decode stage of a Receive pipeline.

The properties of the MIME/SMIME decoder pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable MIME/SMIME decoder pipeline component properties.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Allow non MIME message</strong></td>
<td>Set this property to True if you expect that the Receive pipeline may get messages that are not MIME encoded. This option is useful when the MIME/SMIME decoder component is used in a pipeline that receives messages in different forms, for example MIME encoded or standard XML. By default this property is set to False, meaning that component will generate an error if it receives a non-MIME encoded message on input.<br />
<br />
Default Value: False</td>
</tr>
<tr class="even">
<td><strong>Body part content type</strong></td>
<td>Indicates the content type of the MIME part. The MIME part with this content type will become the body part of the BizTalk message.<br />
<br />
Default value: None</td>
</tr>
<tr class="odd">
<td><strong>Body part index</strong></td>
<td>Indicates the 1-based index into the MIME part list. The MIME part at this index in the list will become the body part of the BizTalk message. To disable the selection of body part by index, use a value of 0.<br />
<br />
Default value: 0</td>
</tr>
<tr class="even">
<td><strong>Check revocation list</strong></td>
<td>Set this property to True if you want to check the revocation list for the certificates that senders use for signing messages that are being sent to BizTalk Server. Enabling this option decreases the performance of the component.<br />
<br />
Default Value: True</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/library/aa578392\(v=bts.80\))  
[How to Configure the MIME-SMIME Decoder Pipeline Component](https://msdn.microsoft.com/library/aa578427\(v=bts.80\))  
[MIME-SMIME Decoder Pipeline Component](https://msdn.microsoft.com/library/aa562169\(v=bts.80\))

