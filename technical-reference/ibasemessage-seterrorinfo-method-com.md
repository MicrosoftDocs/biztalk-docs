---
description: "Learn more about: IBaseMessage.SetErrorInfo Method (COM)"
title: IBaseMessage.SetErrorInfo Method (COM)
TOCTitle: IBaseMessage.SetErrorInfo Method (COM)
ms:assetid: f84ec341-bff7-4f00-af8e-a9100ab986c5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562009(v=BTS.80)
ms:contentKeyID: 51533532
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
ms.topic: reference
---

# IBaseMessage.SetErrorInfo Method (COM)

 

Sets the error information.

## Syntax

``` c++
  
          HRESULT IErrorInfo::SetErrorInfo(   
IErrorInfo pErrInfo);  
```

``` vb
  
Sub SetErrorInfo(  
pErrInfo  
As IErrorInfo)  
  
```

#### Parameters

*pErrInfo*  
\[in\] The error information.

*pErrInfo*  
\[in\] The error information.

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
<tr class="even">
<td>E_INVALIDARG</td>
<td>A parameter that is not valid was detected.</td>
</tr>
</tbody>
</table>


## Requirements

**Platforms:**  Windows

## See Also

[IBaseMessage Interface (COM)](ibasemessage-interface-com.md)  
[IBaseMessage Members (COM)](ibasemessage-members-com.md)

