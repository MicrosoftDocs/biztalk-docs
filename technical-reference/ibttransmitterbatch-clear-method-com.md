---
description: "Learn more about: IBTTransmitterBatch.Clear Method (COM)"
title: IBTTransmitterBatch.Clear Method (COM)
TOCTitle: IBTTransmitterBatch.Clear Method (COM)
ms:assetid: 241f001a-46eb-4668-b652-ac2eed962501
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559210(v=BTS.80)
ms:contentKeyID: 51526811
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
ms.topic: reference
dev_langs:
- c++
- vb
---

# IBTTransmitterBatch.Clear Method (COM)

 

Clears the batch if one or more calls to the [TransmitMessage](ibttransmitterbatch-transmitmessage-method-com.md) method failed.

## Syntax

``` c++
  
HRESULT IBTTransmitterBatch::Clear(  
);  
  
```

``` vb
  
Sub Clear
()  
  
```

## Remarks

**Parameters**

None.

None.

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
</tbody>
</table>


**Remarks**

If one or more calls to the [TransmitMessage](ibttransmitterbatch-transmitmessage-method-com.md) method fail, the BizTalk Server Messaging Engine will clear the batch and then deal with the messages in the batch in the following manner:

  - If the message has retries remaining, it will be resubmitted and the BizTalk Server Messaging Engine will use the retry interval stamped on the message.

  - If the retries have been exhausted for this message, the BizTalk Server Messaging Engine will attempt to move the message to the backup transport.

  - If the BizTalk Server Messaging Engine cannot move the message to the backup transport, the BizTalk Server Messaging Engine will suspend the message.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransmitterBatch Interface (COM)](ibttransmitterbatch-interface-com.md)  
[IBTTransmitterBatch Members (COM)](ibttransmitterbatch-members-com.md)

