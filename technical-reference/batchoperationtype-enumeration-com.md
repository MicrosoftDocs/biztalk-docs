---
title: _BatchOperationType Enumeration (COM)
TOCTitle: _BatchOperationType Enumeration (COM)
ms:assetid: b12c20fd-9f2b-4ba3-92b5-3e57d7eaaa07
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578139(v=BTS.80)
ms:contentKeyID: 51530604
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# \_BatchOperationType Enumeration (COM)

 

Defines the types of operations that can occur within a batch.


> [!NOTE]
> <P>For information on using this interface within managed code, see the <CODE>BatchOperationType Enumeration</CODE>.</P>



## Members

<table>
<thead>
<tr class="header">
<th>Member name</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>BT_CancelResponse</strong></td>
<td>6</td>
<td>Corresponds to the <a href="ibttransportbatch-cancelresponsemessage-method-com.md">CancelResponseMessage</a> method on <a href="ibttransportbatch-interface-com.md">IBTTransportBatch</a>.<br />
<br />
A request for a response message was canceled.</td>
</tr>
<tr class="even">
<td><strong>BT_Delete</strong></td>
<td>1</td>
<td>Corresponds to the <a href="ibttransportbatch-deletemessage-method-com.md">DeleteMessage</a> method on <a href="ibttransportbatch-interface-com.md">IBTTransportBatch</a>.<br />
<br />
A message to be deleted was added to the batch.</td>
</tr>
<tr class="odd">
<td><strong>BT_MoveToNextTransport</strong></td>
<td>4</td>
<td>Corresponds to the <code>MoveToNextTransport</code> method on <a href="ibttransportbatch-interface-com.md">IBTTransportBatch</a>.<br />
<br />
A message to be moved to the backup adapter was added to the batch.</td>
</tr>
<tr class="even">
<td><strong>BT_MoveToSuspendQ</strong></td>
<td>2</td>
<td>Corresponds to the <a href="ibttransportbatch-movetosuspendq-method-com.md">MoveToSuspendQ</a> method on <a href="ibttransportbatch-interface-com.md">IBTTransportBatch</a>.<br />
<br />
A message to be suspended was added to the batch.</td>
</tr>
<tr class="odd">
<td><strong>BT_Resubmit</strong></td>
<td>3</td>
<td>Corresponds to the <a href="ibttransportbatch-resubmit-method-com.md">Resubmit</a> method on <a href="ibttransportbatch-interface-com.md">IBTTransportBatch</a>.<br />
<br />
A message to be resubmitted was added to the batch.</td>
</tr>
<tr class="even">
<td><strong>BT_Submit</strong></td>
<td>0</td>
<td>Corresponds to the <a href="ibttransportbatch-submitmessage-method-com.md">SubmitMessage</a> method on <a href="ibttransportbatch-interface-com.md">IBTTransportBatch</a>.<br />
<br />
A message to be submitted was added to the batch.</td>
</tr>
<tr class="odd">
<td><strong>BT_SubmitRequest</strong></td>
<td>5</td>
<td>Corresponds to the <a href="ibttransportbatch-submitrequestmessage-method-com.md">SubmitRequestMessage</a> method on <a href="ibttransportbatch-interface-com.md">IBTTransportBatch</a>.<br />
<br />
A request message for a request-response message exchange was added to the batch.</td>
</tr>
</tbody>
</table>

