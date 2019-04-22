---
title: IBTTransportControl.Initialize Method (COM)
TOCTitle: IBTTransportControl.Initialize Method (COM)
ms:assetid: 861280f6-75e9-4f7b-a5ad-4175a1bb51a9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561188(v=BTS.80)
ms:contentKeyID: 51529420
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportControl.Initialize Method (COM)

 

Initializes the adapter.

## Syntax

``` c++
  
HRESULT IBTTransportControl::Initialize(  
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

## Remarks

**Parameters**

*pTransProxy*  
\[in\] Reference to a **IBTTransportProxy** object/interface that contains the transport proxy for the adapter. Each adapter has its own dedicated transport proxy.

*pTransProxy*  
**IBTTransportProxy** object/interface that contains the transport proxy for the adapter. Each adapter has its own dedicated transport proxy.

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

This method is called by the BizTalk Server Messaging Engine.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportControl Interface (COM)](ibttransportcontrol-interface-com.md)  
[IBTTransportControl Members (COM)](ibttransportcontrol-members-com.md)

