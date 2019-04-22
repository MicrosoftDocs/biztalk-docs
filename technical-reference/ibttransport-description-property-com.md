---
title: IBTTransport.Description Property (COM)
TOCTitle: IBTTransport.Description Property (COM)
ms:assetid: 33d68ae9-e67c-4f0f-8b5b-26dea7e8f46e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559525(v=BTS.80)
ms:contentKeyID: 51527266
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransport.Description Property (COM)

 

Gets the component description.

## Syntax

``` c++
  
HRESULT IBTTransport::get_Description(  
BSTR*  
Description  
);  
  
```

``` vb
  
Property Description
() As String  
  
```

## Remarks

**Parameters**

*Description*  
\[out,retval\] String used to return the description of the component.

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

