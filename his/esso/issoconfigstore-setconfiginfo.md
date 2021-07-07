---
description: "Learn more about: ISSOConfigStore::SetConfigInfo"
title: "ISSOConfigStore::SetConfigInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84dac951-3894-43c8-9e19-1d260ef47ef5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# ISSOConfigStore::SetConfigInfo

The **SetConfigInfo** method sets the configuration information in the config store.  
  
## Syntax  
  
```cpp  
  
HRESULT SetConfigInfo(  
BSTR bstrApplication,  
BSTR bstrIdentifier,  
IPropertyBag* ppbConfigInfo  
);  
```  
  
```vb  
  
SetConfigInfo(  
bstrApplication As BSTR,  
bstrIdentifier As BSTR,  
ppbConfigInfo As IPropertyBag  
)  
```  
  
## Parameters
  
 `bstrApplication`  
 [in]  String containing the external application name.  
  
 `bstrApplication`  
 [in]  String containing the external application name.  
  
 `bstrIdentifier`  
 [in]  String containing the identifier for the config info. This string will typically be a GUID.  
  
 `bstrIdentifier`  
 [in]  String containing the identifier for the config info. This string will typically be a GUID.  
  
 `ppbConfigInfo`  
 [in]  Contains a pointer to a property bag containing the config info as name/value pairs.  
  
 `ppbConfigInfo`  
 [in]  Contains a pointer to a property bag containing the config info as name/value pairs.  
  
## Return Values
  
This method does not return a value.  
  
The method returns an **HRESULT**. Possible values include, but are not limited to, those in the following table.  
  
|Return code|Description|  
|-----------------|-----------------|  
|S_OK|The config info was successfully stored in the config store.|  
|E_ACCESSDENIED|Access denied.|  
|E_INVALIDARG|Invalid argument.|  
  
## Remarks
  
This method can be used for originally creating the config info or for updating the config info.  
  
If the config info does not already exist, all properties of the config info, as defined by the field info for the specified application, must be provided.  
  
If the config info does already exist, a property within the config info can be missing. Only properties that are provided will be updated. At least one property must be provided.  
  
Note that due to the use of the Single Sign-On (SSO) store, the first property cannot be masked.  
  
If the ***bstrSSOServer*** parameter is NULL, the SSO server location is obtained from the registry. If not available in the registry, the local computer will be used.  
  
## Example  
  
```csharp
  
ConfigStore  
bstrApplication  
bstrIdentifier  
ppbConfigInfo  
  
```  
  
## See Also

[ISSOConfigStore::GetConfigInfo](../esso/issoconfigstore-getconfiginfo.md)   
[ISSOConfigStore Interface (COM)](../esso/issoconfigstore-interface-com.md)   
[Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)
