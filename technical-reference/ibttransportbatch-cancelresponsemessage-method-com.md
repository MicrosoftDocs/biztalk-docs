---
description: "Learn more about: IBTTransportBatch.CancelResponseMessage Method (COM)"
title: IBTTransportBatch.CancelResponseMessage Method (COM)
TOCTitle: IBTTransportBatch.CancelResponseMessage Method (COM)
ms.topic: reference
ms:assetid: 97afd5ed-694a-4b96-804c-2f57ef81e355
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577461(v=BTS.80)
ms:contentKeyID: 51529876
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.CancelResponseMessage Method (COM)

 

Adds a cancellation request to the batch to cancel a request for a response message.

## Syntax

``` c++
  
HRESULT IBTTransportBatch::CancelResponseMessage(  
BSTR  
bstrCorrelationToken  
);  
  
```

``` vb
  
Sub CancelResponseMessage(  
bstrCorrelationToken  
 As String  
)  
  
```

## Remarks

**Parameters**

*bstrCorrelationToken*  
\[in\] String that contains the correlation token of the message that a response was requested for.

*bstrCorrelationToken*  
**String** that contains the correlation token of the message that a response was requested for.

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


**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

