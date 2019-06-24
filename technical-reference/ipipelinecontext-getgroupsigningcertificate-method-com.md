---
title: IPipelineContext.GetGroupSigningCertificate Method (COM)
TOCTitle: IPipelineContext.GetGroupSigningCertificate Method (COM)
ms:assetid: dee7be36-2968-44a5-a76a-5d565d7e71dd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561483(v=BTS.80)
ms:contentKeyID: 51532839
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# IPipelineContext.GetGroupSigningCertificate Method (COM)

 

Get access to the helper interface to work with BizTalk Server message objects.

## Syntax

``` c++
  
HRESULT IPipelineContext::GetGroupSigningCertificate(  
BSTR**  
ppRet  
);  
  
```

``` vb
  
Function GetGroupSigningCertificate
() As String  
  
```

#### Parameters

*ppRet*  
\[out,retval\] Pointer to hold the reference to the returned **String** containing the signing certificate for the group.

None.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.

If this method completes successfully, it returns the [IBaseMessageFactory](ibasemessagefactory-interface-com.md) associated with the pipeline context.

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

[IPipelineContext Interface (COM)](ipipelinecontext-interface-com.md)  
[IPipelineContext Members (COM)](ipipelinecontext-members-com.md)

