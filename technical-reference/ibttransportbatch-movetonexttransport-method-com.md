---
title: IBTTransportBatch.MoveToNextTransport Method (COM)
TOCTitle: IBTTransportBatch.MoveToNextTransport Method (COM)
ms:assetid: de2eb846-709d-403e-80a8-577826d5f459
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561470(v=BTS.80)
ms:contentKeyID: 51532821
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.MoveToNextTransport Method (COM)

 

Adds a message to the batch to be moved to the backup transport.

## Syntax

``` c++
  
            HRESULT IBTTransportBatch::MoveToNextTransport(  
            IBaseMessage*  
            pIndoc,  
);  
```

``` vb
  
            Sub MoveToNextTransport(  
            pIndoc  
             As IBaseMessage,  
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

This message should only be called on the send-side.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

