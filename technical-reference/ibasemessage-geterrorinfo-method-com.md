---
title: IBaseMessage.GetErrorInfo Method (COM)
TOCTitle: IBaseMessage.GetErrorInfo Method (COM)
ms:assetid: 1b68d601-fafb-4604-b1c3-171ab6072d66
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559059(v=BTS.80)
ms:contentKeyID: 51526570
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBaseMessage.GetErrorInfo Method (COM)

 

Gets the exception that caused the error.

## Syntax

``` c++
  
HRESULT IErrorInfo::GetErrorInfo(  
);  
  
```

``` vb
  
Function GetErrorInfo(  
) As IErrorInfo  
  
```

#### Parameters

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

## Error Values

This method returns an HRESULT containing one of the values in the following table.

This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.

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

**Platforms:** Windows

## See Also

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)  
[IBaseMessage Members (COM)](ibasemessage-members-com.md)

