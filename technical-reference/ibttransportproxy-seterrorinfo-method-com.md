---
title: IBTTransportProxy.SetErrorInfo Method (COM)
TOCTitle: IBTTransportProxy.SetErrorInfo Method (COM)
ms:assetid: f05983ae-1c10-4724-9aa0-17de892730a6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561841(v=BTS.80)
ms:contentKeyID: 51533297
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IBTTransportProxy.SetErrorInfo Method (COM)

 

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

## Remarks

**Parameters**

*pErrInfo*  
\[in\] The error information.

*pErrInfo*  
\[in\] The error information.

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

[IBTTransportProxy Interface (COM)](ibttransportproxy-interface-com.md)  
[IBTTransportProxy Members (COM)](ibttransportproxy-members-com.md)

