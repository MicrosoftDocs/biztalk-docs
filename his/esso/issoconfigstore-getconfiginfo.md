---
title: "ISSOConfigStore::GetConfigInfo | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38dfe88c-93a8-4b44-8729-9f8b1cafa98c
caps.latest.revision: 3
---
# ISSOConfigStore::GetConfigInfo
The `GetConfigInfo` method gets the configuration information from the config store.  
  
## Syntax  
  
```cpp#  
  
HRESULT GetConfigInfo(  
BSTR bstrApplication,  
BSTR bstrIdentifier,  
LONG lFlags,  
IPropertyBag* ppbConfigInfo  
);  
```  
  
```vb  
  
GetConfigInfo(  
bstrApplication As BSTR,  
bstrIdentifier As BSTR,  
lFlags As LONG,  
ppbConfigInfo As IPropertyBag  
)  
```  
  
#### Parameters  
 `bstrApplication`  
 [in]  String containing the Single Sign-On (SSO) server. This property is optional.  
  
 `bstrApplication`  
 [in]  String containing the SSO server. This property is optional.  
  
 `bstrIdentifier`  
 [in]  String containing the identifier for the config info. This string is typically a GUID string.  
  
 `bstrIdentifier`  
 [in]  String containing the identifier for the config info. This string is typically a GUID string.  
  
 `lFlags`  
 [in]  Long integer containing the flags.  
  
 `lFlags`  
 [in]  Long integer containing the flags.  
  
 `ppbConfigInfo`  
 [in]  Pointer to an empty property bag that is populated with the config info as name/value pairs.  
  
 `ppbConfigInfo`  
 [in]  Pointer to an empty property bag that is populated with the config info as name/value pairs.  
  
## Return Value  
 This method does not return a value.  
  
 The method returns an **HRESULT**. Possible values include, but are not limited to, those in the following table.  
  
|Return code|Description|  
|-----------------|-----------------|  
|S_OK|The config info was successfully returned from the config store.|  
|E_ACCESSDENIED|Access denied.|  
|E_INVALIDARG|Invalid argument.|  
  
## Remarks  
 This method can be executed either in admin or run-time (lookup) mode. The caller specifies SSO_FLAG_LOOKUP if the run-time (lookup) mode is required. The default mode is admin mode.  
  
 In admin mode, masked properties are not returned. Instead, the property is missing. Unmasked properties are returned. Admin mode can specify any SSO server, not just the local computer.  
  
 In run-time mode, all properties, including masked properties, are returned. Because run-time mode only uses the SSO server on the current computer, the *bstrSSOServer* parameter will be ignored.  
  
 If the *bstrSSOServer* parameter is NULL, the SSO server location is obtained from the registry. (This applies to admin mode only. Run-time mode always uses the local computer.) If the server location is not available in the registry, the local computer is used.  
  
 To get the config info, this method is provided with an empty property bag that is populated with the properties. This allows the [!INCLUDE[btsBizTalkServer2006](../esso/includes/btsbiztalkserver2006-md.md)] implementation of the property bag to be used, which can handle the type conversion from BSTRs to the actual variant types based on a format convention specific to [!INCLUDE[btsBizTalkServer2006](../esso/includes/btsbiztalkserver2006-md.md)]. The property values will be XML tags for Host Integration Server.  
  
## Example Code  
  
```  
  
ConfigStore  
bstrApplication  
bstrIdentifier  
lFlags  
ppbConfigInfo  
  
```  
  
## See Also  
 [ISSOConfigStore Interface (COM)](../esso/issoconfigstore-interface-com.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)