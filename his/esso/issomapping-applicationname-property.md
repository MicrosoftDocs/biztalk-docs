---
description: "Learn more about: ISSOMapping.ApplicationName Property"
title: "ISSOMapping.ApplicationName Property | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a5be3cc-c88b-42b5-af02-539384463624
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# ISSOMapping.ApplicationName Property
The **ApplicationName** property specifies the name of the application.  
  
## Syntax  
  
```cpp  
  
HRESULT ISSOMapping::get_ApplicationName(  
BSTR* ApplicationName  
);  
HRESULT ISSOMapping::put_ApplicationName(  
BSTR ApplicationName  
);  
```  
  
```vb  
  
Property ApplicationName() As String  
  
```  
  
#### Parameters  
 `ApplicationName`  
 [in] When putting the property, a string that contains the application name. [out, retval] When getting the property, a string used to return the application name.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOMapping Interface (COM)](../esso/issomapping-interface-com.md)   
 [ISSOMapping Members](../esso/issomapping-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)
