---
description: "Learn more about: IBTTransportBatch.SubmitMessage Method (COM)"
title: IBTTransportBatch.SubmitMessage Method (COM)
TOCTitle: IBTTransportBatch.SubmitMessage Method (COM)
ms:assetid: f821d270-bc2e-4237-976c-6862286d3be9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562006(v=BTS.80)
ms:contentKeyID: 51533498
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.SubmitMessage Method (COM)

 

Adds a message to the batch to be processed by the BizTalk Server Messaging Engine.

## Syntax

``` c++
  
HRESULT IBTTransportBatch::SubmitMessage(  
IBaseMessage*  
pIndoc  
);  
  
```

``` vb
  
Sub SubmitMessage(  
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
<td>BTS_E_URL_DISALLOWED</td>
<td>The URL specified on the message context was not valid at the time the API was called.</td>
</tr>
<tr class="odd">
<td>E_INVALIDARG</td>
<td>A parameter that is not valid was detected.</td>
</tr>
</tbody>
</table>


**Remarks**

The context properties ***InboundTransportLocation*** and ***InboundTransportType*** should be present in the message context; this is used to look up the receive port configuration for this URL.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportBatch Interface (COM)](ibttransportbatch-interface-com.md)  
[IBTTransportBatch Members (COM)](ibttransportbatch-members-com.md)

