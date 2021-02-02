---
description: "Learn more about: IBTTransportControl.Terminate Method (COM)"
title: IBTTransportControl.Terminate Method (COM)
TOCTitle: IBTTransportControl.Terminate Method (COM)
ms:assetid: 0022ba49-0c5e-49af-8558-b5b032788687
ms:mtpsurl: https://msdn.microsoft.com/library/Aa546730(v=BTS.80)
ms:contentKeyID: 51525827
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportControl.Terminate Method (COM)

 

Finishes processing any messages the adapter is currently processing and prepares for termination.

## Syntax

``` c++
  
HRESULT IBTTransportControl::Terminate(  
);  
  
```

``` vb
  
Sub Terminate
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

This method is called by the BizTalk Server Messaging Engine.

The adapter should not start any new work after this call, but may complete outstanding work items as necessary.

**Requirements**

**Platforms:**  Windows

## See Also

[IBTTransportControl Interface (COM)](ibttransportcontrol-interface-com.md)  
[IBTTransportControl Members (COM)](ibttransportcontrol-members-com.md)

