---
description: "Learn more about: IBTTransport.Version Property (COM)"
title: IBTTransport.Version Property (COM)
TOCTitle: IBTTransport.Version Property (COM)
ms:assetid: e7a624e4-61fd-4369-83e5-2cbaffc004e2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561659(v=BTS.80)
ms:contentKeyID: 51533056
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransport.Version Property (COM)

 

Gets the component version.

## Syntax

``` c++
  
HRESULT IBTTransport::get_Version(  
BSTR*  
Version  
);  
  
```

``` vb
  
Property Version() As String  
  
```

## Remarks

**Parameters**

*Version*  
\[out,retval\] String used to return the version of the component.

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

