---
title: ISSOConfigStore::DeleteConfigInfo
TOCTitle: ISSOConfigStore::DeleteConfigInfo
ms:assetid: 8b6abd92-6108-4c16-a075-7306f9381f34
ms:mtpsurl: https://msdn.microsoft.com/library/Aa745566(v=BTS.80)
ms:contentKeyID: 51529557
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOConfigStore::DeleteConfigInfo

 

The **DeleteConfigInfo** method deletes the configuration information from the config store.

## Syntax

``` c++
  
HRESULT DeleteConfigInfo(  
BSTR bstrApplication,  
BSTR bstrIdentifier,  
);  
```

``` vb
  
DeleteConfigInfo(  
bstrApplication As BSTR,  
bstrIdentifier As BSTR,  
)  
```

#### Parameters

`bstrApplication`  
\[in\] String containing the external application name.

`bstrApplication`  
\[in\] String containing the external application name.

`bstrIdentifier`  
\[in\] String containing the identifier for the config info. This will typically be a GUID string.

`bstrIdentifier`  
\[in\] String containing the identifier for the config info. This will typically be a GUID string.

## Return Value

This method does not return a value.

The method returns an **HRESULT**. Possible values include, but are not limited to, those in the following table.

<table>
<thead>
<tr class="header">
<th>Return code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>S_OK</td>
<td>The config info was successfully returned from the config store.</td>
</tr>
<tr class="even">
<td>S_FALSE</td>
<td>The config info did not already exist.</td>
</tr>
<tr class="odd">
<td>E_ACCESSDENIED</td>
<td>Access denied.</td>
</tr>
<tr class="even">
<td>E_INVALIDARG</td>
<td>Invalid argument.</td>
</tr>
</tbody>
</table>


## Remarks

If the config info specified by the parameters does not already exist in the config store, this method will return S\_FALSE.

If the *bstrSSOServer* parameter is NULL, the Single Sign-On (SSO) server location is obtained from the registry. If the server location is not available in the registry, the local computer is used.

## Example

```C#
  
ConfigStore  
bstrApplication  
bstrIdentifier  
  
```

## See Also

[ISSOConfigStore Interface (COM)](issoconfigstore-interface-com.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

