---
description: "Learn more about: IBTTransmitterBatch.Done Method (COM)"
title: IBTTransmitterBatch.Done Method (COM)
TOCTitle: IBTTransmitterBatch.Done Method (COM)
ms:assetid: b3a11a9b-de6a-494a-9335-47678c20a510
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578191(v=BTS.80)
ms:contentKeyID: 51530665
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
dev_langs:
- c++
- vb
---

# IBTTransmitterBatch.Done Method (COM)

 

Indicates to an adapter that the batch is completed and is ready to be sent.

## Syntax

``` c++
  
HRESULT IBTTransmitterBatch::Done(  
IBTDTCCommitConfirm*  
pDTCCommitConfirm  
);  
  
```

``` vb
  
Sub Done(  
pDTCCommitConfirm  
 As IBTDTCCommitConfirm  
)  
  
```

## Remarks

**Parameters**

*pDTCCommitConfirm*  
\[in\] Reference to a **IBTDTCCommitConfirm** object/interface that contains the DTC commit confirm. If the adapter is not using transactions for transmissions, this parameter will be NULL. If this parameter is not NULL, which means the adapter is using DTC transactions, the adapter is required to callback to inform the BizTalk Server Messaging Engine the outcome of the transaction.

*pDTCCommitConfirm*  
**IBTDTCCommitConfirm** object/interface that contains the DTC commit confirm. If the adapter is not using transactions for transmissions, this parameter will be NULL. If this parameter is not NULL, which means the adapter is using DTC transactions, the adapter is required to callback to inform the BizTalk Server Messaging Engine the outcome of the transaction.

**Return Values**

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

None.

**Error Values**

This method returns an HRESULT containing one of the values in the following table.

This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>S_OK</td>
<td>The method completed successfully.</td>
</tr>
<tr class="even">
<td>FAILED HRESULT</td>
<td>If the <strong>Done</strong> method fails, the Messaging Engine will deal with all of the individual messages in the batch in the following manner:<br />
<br />
- If the message has retries remaining, it will be resubmitted, the Messaging Engine will use the retry interval stamped on the message.<br />
- If the retries have been exhausted for this message, the Messaging Engine will attempt to move the message to the backup transport.<br />
- If the Messaging Engine cannot move the message to its backup transport, the Messaging Engine will suspend the message.</td>
</tr>
</tbody>
</table>


**Remarks**

This method is called by the BizTalk Server Messaging Engine when either the batch is full or the BizTalk Server Messaging Engine does not have any more messages for this batch. The adapter will transmit all the messages in the batch when the **Done** method is called.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransmitterBatch Interface (COM)](ibttransmitterbatch-interface-com.md)  
[IBTTransmitterBatch Members (COM)](ibttransmitterbatch-members-com.md)

