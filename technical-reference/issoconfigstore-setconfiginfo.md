---
title: ISSOConfigStore::SetConfigInfo
TOCTitle: ISSOConfigStore::SetConfigInfo
ms:assetid: 58b49e87-862d-4dbe-a382-d699494ab29a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa770934(v=BTS.80)
ms:contentKeyID: 51528201
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOConfigStore::SetConfigInfo

 

The **SetConfigInf**o method sets the configuration information in the config store.

## Syntax

``` c++
  
HRESULT SetConfigInfo(  
BSTR bstrApplication,  
BSTR bstrIdentifier,  
IPropertyBag* ppbConfigInfo  
);  
```

``` vb
  
SetConfigInfo(  
bstrApplication As BSTR,  
bstrIdentifier As BSTR,  
ppbConfigInfo As IPropertyBag  
)  
```

## Remarks

`bstrApplication`  
\[in\] String containing the external application name.

`bstrApplication`  
\[in\] String containing the external application name.

`bstrIdentifier`  
\[in\] String containing the identifier for the config info. This string will typically be a GUID.

`bstrIdentifier`  
\[in\] String containing the identifier for the config info. This string will typically be a GUID.

`ppbConfigInfo`  
\[in\] Contains a pointer to a property bag containing the config info as name/value pairs.

`ppbConfigInfo`  
\[in\] Contains a pointer to a property bag containing the config info as name/value pairs.

## Return Values

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
<td>The config info was successfully stored in the config store.</td>
</tr>
<tr class="even">
<td>E_ACCESSDENIED</td>
<td>Access denied.</td>
</tr>
<tr class="odd">
<td>E_INVALIDARG</td>
<td>Invalid argument.</td>
</tr>
</tbody>
</table>


## Remarks

This method can be used for originally creating the config info or for updating the config info.

If the config info does not already exist, all properties of the config info, as defined by the field info for the specified application, must be provided.

If the config info does already exist, a property within the config info can be missing. Only properties that are provided will be updated. At least one property must be provided.

Note that due to the use of the Single Sign-On (SSO) store, the first property cannot be masked.

If the ***bstrSSOServer*** parameter is NULL, the SSO server location is obtained from the registry. If not available in the registry, the local computer will be used.

## Example

```C#
  
ConfigStore  
bstrApplication  
bstrIdentifier  
ppbConfigInfo  
  
```

## See Also

[ISSOConfigStore::GetConfigInfo](issoconfigstore-getconfiginfo.md)  
[ISSOConfigStore Interface (COM)](issoconfigstore-interface-com.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

