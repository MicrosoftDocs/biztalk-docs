---
description: "Learn more about: IBTTransmitter.Terminate Method (COM)"
title: IBTTransmitter.Terminate Method (COM)
TOCTitle: IBTTransmitter.Terminate Method (COM)
ms:assetid: 77b8eee7-3fd8-4083-a73f-c155f0df9255
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560891(v=BTS.80)
ms:contentKeyID: 51529041
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
dev_langs:
- c++
- vb
---

# IBTTransmitter.Terminate Method (COM)

 

Finishes processing any messages the adapter is currently processing and prepares for termination.

## Syntax

``` c++
  
HRESULT IBTTransmitter::Terminate(  
);  
  
```

``` vb
  
Sub Terminate
()  
  
```

#### Parameters

None.

None.

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

The adapter should not start any new work after this call, but may complete outstanding work items as necessary.

## Requirements

**Platforms:**  Windows

## See Also

[IBTTransmitter Interface (COM)](ibttransmitter-interface-com.md)  
[IBTTransmitter Members (COM)](ibttransmitter-members-com.md)

