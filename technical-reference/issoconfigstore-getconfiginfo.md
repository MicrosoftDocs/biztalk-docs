---
description: "Learn more about: ISSOConfigStore::GetConfigInfo"
title: ISSOConfigStore::GetConfigInfo
TOCTitle: ISSOConfigStore::GetConfigInfo
ms:assetid: 2e9d479e-2018-45b2-b951-574b7d3d2cb5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa745237(v=BTS.80)
ms:contentKeyID: 51527134
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- c++
- vb
---

# ISSOConfigStore::GetConfigInfo

 

The `GetConfigInfo` method gets the configuration information from the config store.

## Syntax

``` c++
  
HRESULT GetConfigInfo(  
BSTR bstrApplication,  
BSTR bstrIdentifier,  
LONG lFlags,  
IPropertyBag* ppbConfigInfo  
);  
```

``` vb
  
GetConfigInfo(  
bstrApplication As BSTR,  
bstrIdentifier As BSTR,  
lFlags As LONG,  
ppbConfigInfo As IPropertyBag  
)  
```

#### Parameters

`bstrApplication`  
\[in\] String containing the Single Sign-On (SSO) server. This property is optional.

`bstrApplication`  
\[in\] String containing the SSO server. This property is optional.

`bstrIdentifier`  
\[in\] String containing the identifier for the config info. This string is typically a GUID string.

`bstrIdentifier`  
\[in\] String containing the identifier for the config info. This string is typically a GUID string.

`lFlags`  
\[in\] Long integer containing the flags.

`lFlags`  
\[in\] Long integer containing the flags.

`ppbConfigInfo`  
\[in\] Pointer to an empty property bag that is populated with the config info as name/value pairs.

`ppbConfigInfo`  
\[in\] Pointer to an empty property bag that is populated with the config info as name/value pairs.

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

This method can be executed either in admin or run-time (lookup) mode. The caller specifies SSO\_FLAG\_LOOKUP if the run-time (lookup) mode is required. The default mode is admin mode.

In admin mode, masked properties are not returned. Instead, the property is missing. Unmasked properties are returned. Admin mode can specify any SSO server, not just the local computer.

In run-time mode, all properties, including masked properties, are returned. Because run-time mode only uses the SSO server on the current computer, the *bstrSSOServer* parameter will be ignored.

If the *bstrSSOServer* parameter is NULL, the SSO server location is obtained from the registry. (This applies to admin mode only. Run-time mode always uses the local computer.) If the server location is not available in the registry, the local computer is used.

To get the config info, this method is provided with an empty property bag that is populated with the properties. This allows the BizTalk Server 2006 implementation of the property bag to be used, which can handle the type conversion from BSTRs to the actual variant types based on a format convention specific to BizTalk Server 2006. The property values will be XML tags for Host Integration Server.

## Example Code

```C#
  
ConfigStore  
bstrApplication  
bstrIdentifier  
lFlags  
ppbConfigInfo  
  
```

## See Also

[ISSOConfigStore Interface (COM)](issoconfigstore-interface-com.md)  
[Programming with Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa704508\(v=bts.80\))

