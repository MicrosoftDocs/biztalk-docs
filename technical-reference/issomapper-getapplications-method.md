---
title: ISSOMapper.GetApplications Method
TOCTitle: ISSOMapper.GetApplications Method
ms:assetid: 69099b5a-7844-4945-9af6-6267c14ce8e7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa771299(v=BTS.80)
ms:contentKeyID: 51528641
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOMapper.GetApplications Method

 

The **GetApplications** method retrieves the available applications for a Microsoft Windows user.

## Syntax

``` c++
  
HRESULT GetApplications(  
SAFEARRAY applications,  
SAFEARRAY descriptions,  
SAFEARRAY contactInfo  
)  
```

``` vb
  
Sub GetApplications(  
applications As String,  
descriptions As String,   
contactInfo As String  
)  
```

#### Parameters

`applications`  
\[out\] String array that returns the application name.

`applications`  
\[out\] String array that returns the application name.

`descriptions`  
\[out\] String array that returns a description for the application.

`descriptions`  
\[out\] String array that returns a description for the application.

`contactInfo`  
\[out\] String array that returns the contact information for the application.

`contactInfo`  
\[out\] String array that returns the contact information for the application.

## Return Value

This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.

Not applicable.

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
<td>The method succeeded.</td>
</tr>
<tr class="even">
<td>E_INVALIDARG</td>
<td>An invalid parameter was detected.</td>
</tr>
</tbody>
</table>


## Requirements

**Platforms:**  Windows

## See Also

[ISSOMapper Interface (COM)](issomapper-interface-com.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/en-us/library/aa704508\(v=bts.80\))

