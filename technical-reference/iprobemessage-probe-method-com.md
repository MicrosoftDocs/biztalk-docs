---
description: "Learn more about: IProbeMessage.Probe Method (COM)"
title: IProbeMessage.Probe Method (COM)
TOCTitle: IProbeMessage.Probe Method (COM)
ms:assetid: 1fefbfe0-0eb4-4544-88a5-96164bfdd25f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559139(v=BTS.80)
ms:contentKeyID: 51526681
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IProbeMessage.Probe Method (COM)

 

Checks if the incoming message is in a recognizable format.

## Syntax

``` c++
  
        HRESULT IProbeMessage::Probe(  
        IPipelineContext*  
        pContext,  
IBaseMessage*pInMsg,  
VARIANT_BOOL*pRet);  
```

``` vb
  
        Function Probe(  
        pContext  
         As IPipelineContext,  
pInMsg As IBaseMessage) As Boolean  
```

#### Parameters

*pContext*  
\[in\] Reference to a **IPipelineContext** object/interface that contains the current pipeline context.

*pContext*  
**IPipelineContext** object/interface that contains the current pipeline context.

*pInMsg*  
\[in\] Reference to a **IBaseMessage** object/interface that contains the incoming message.

*pInMsg*  
**IBaseMessage** object/interface that contains the incoming message.

*pRet*  
\[out,retval\] Pointer to a Variant Boolean. **true** if the format was recognized; otherwise, **false**

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns **true** if the format was recognized; otherwise, **false**.

## Error Values

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


## Requirements

**Platforms:**  Windows

## See Also

[IProbeMessage Interface (COM)](iprobemessage-interface-com.md)  
[IProbeMessage Members (COM)](iprobemessage-members-com.md)

