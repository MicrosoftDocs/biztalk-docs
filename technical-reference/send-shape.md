---
title: Send Shape
TOCTitle: Send Shape
ms:assetid: f5561659-ae7a-423e-a254-60586ca32cef
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561950(v=BTS.80)
ms:contentKeyID: 51533456
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.orch.shape.send
---

# Send Shape

 

Use the **Send** shape to send a given message to a specified port. If you expect to receive an indirect response (not using a request-response port) to the message that you have sent, you will need to correlate the message with the currently running instance of the orchestration, so that the respondent can get the response to the correct instance. You can apply a following correlation set to the Send shape for a previously initialized correlation, or you can apply an initializing correlation set.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Following Correlation Sets</strong> property</td>
<td>From the drop-down list, select already-initialized correlation sets.</td>
</tr>
<tr class="even">
<td><strong>Initializing Correlation Sets</strong> property</td>
<td>From the drop-down list, select the correlation sets which will be initialized by the values in the sent message.</td>
</tr>
<tr class="odd">
<td><strong>Message</strong> property</td>
<td>Specify the message to be sent.</td>
</tr>
<tr class="even">
<td><strong>Operation</strong> property</td>
<td>Specify the operation in which to send the message.</td>
</tr>
<tr class="odd">
<td><strong>Report to Analyst</strong> property</td>
<td>Select <strong>True</strong> if you want to make this shape viewable in the Visual Business Analyst Tool.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure the Send Shape](https://msdn.microsoft.com/en-us/library/aa559388\(v=bts.80\))

