---
description: "Learn more about: IBTTransmitter.Initialize Method (COM)"
title: IBTTransmitter.Initialize Method (COM)
TOCTitle: IBTTransmitter.Initialize Method (COM)
ms:assetid: bd9ebee4-1e45-4cf2-a14d-f2e8d7e708c2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578388(v=BTS.80)
ms:contentKeyID: 51530880
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransmitter.Initialize Method (COM)

 

Initializes the adapter.

## Syntax

``` c++
  
HRESULT IBTTransmitter::Initialize(  
IBTTransportProxy*  
pTransProxy  
);  
  
```

``` vb
  
Sub Initialize(  
pTransProxy  
 As IBTTransportProxy  
)  
  
```

#### Parameters

*pTransProxy*  
\[in\] Reference to a **IBTTransportProxy** object/interface that contains the transport proxy for the adapter. Each adapter has its own dedicated transport proxy.

*pTransProxy*  
**IBTTransportProxy** object/interface that contains the transport proxy for the adapter. Each adapter has its own dedicated transport proxy.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

None.

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
</tbody>
</table>


## Remarks

This method is called by the BizTalk Server Messaging Engine.

## Requirements

**Platforms:**  Windows

## See Also

[IBTTransmitter Interface (COM)](ibttransmitter-interface-com.md)  
[IBTTransmitter Members (COM)](ibttransmitter-members-com.md)

