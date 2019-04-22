---
title: IBTTransport.Name Property (COM)
TOCTitle: IBTTransport.Name Property (COM)
ms:assetid: 1e3d4eb6-d245-4ad1-bf33-f8d81bc44277
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559110(v=BTS.80)
ms:contentKeyID: 51526671
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransport.Name Property (COM)

 

Gets the component name.

## Syntax

``` c++
  
HRESULT IBTTransport::get_Name(  
BSTR*  
Name  
);  
  
```

``` vb
  
Property Name
() As String  
  
```

## Remarks

**Parameters**

*Name*  
\[out,retval\] String used to return the name of the component.

None.

**Return Values**

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

Not applicable.

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

[IBTTransport Interface (COM)](ibttransport-interface-com.md)  
[IBTTransport Members (COM)](ibttransport-members-com.md)

