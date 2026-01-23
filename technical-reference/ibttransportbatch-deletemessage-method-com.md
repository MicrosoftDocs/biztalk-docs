---
description: "Learn more about: IBTTransportBatch.DeleteMessage Method (COM)"
title: IBTTransportBatch.DeleteMessage Method (COM)
TOCTitle: IBTTransportBatch.DeleteMessage Method (COM)
ms.topic: reference
ms:assetid: c556ef11-2db1-4d2e-ae84-e0300ab6ec86
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547897(v=BTS.80)
ms:contentKeyID: 51531054
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.DeleteMessage Method (COM)

 

Adds a message to the batch to be deleted.

## Syntax

``` c++
  
HRESULT IBTTransportBatch::DeleteMessage(  
IBaseMessage*  
pIndoc  
);  
  
```

``` vb
  
Sub DeleteMessage(  
pIndoc  
 As IBaseMessage  
)  
  
```

## Remarks

**Parameters**

*pIndoc*  
\[in\] Reference to a **IBaseMessage** object/interface that contains the message to be added to the batch.

*pIndoc*  
**IBaseMessage** object/interface that contains the message to be added to the batch.

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
<td>E_INVALIDARG</td>
<td>A parameter that is not valid was detected.</td>
</tr>
</tbody>
</table>


**Remarks**

Adapters should call this method if they are sending messages asynchronously; once the message has been successfully transmitted the message needs to be deleted. If the message is sent synchronously, the message engine automatically deletes the message.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

