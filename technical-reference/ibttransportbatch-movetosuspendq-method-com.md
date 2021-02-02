---
description: "Learn more about: IBTTransportBatch.MoveToSuspendQ Method (COM)"
title: IBTTransportBatch.MoveToSuspendQ Method (COM)
TOCTitle: IBTTransportBatch.MoveToSuspendQ Method (COM)
ms:assetid: d20040f1-9194-4d51-98eb-55229a1e9d01
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578551(v=BTS.80)
ms:contentKeyID: 51531538
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportBatch.MoveToSuspendQ Method (COM)

 

Adds a message to the batch to be suspended.

## Syntax

``` c++
  
            HRESULT IBTTransportBatch::MoveToSuspendQ(  
            IBaseMessage*  
            pIndoc,  
);  
```

``` vb
  
            Sub MoveToSuspendQ(  
            pIndoc  
             As IBaseMessage,  
)  
```

## Remarks

**Parameters**

*pIndoc*  
\[in\] Reference to a **IBaseMessage** object/interface that contains the message to be suspended.

*pIndoc*  
**IBaseMessage** object/interface that contains the message to be suspended.

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

