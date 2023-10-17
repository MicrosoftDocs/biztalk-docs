---
description: "Learn more about: ISSOMapping.WindowsUserName Property"
title: "ISSOMapping.WindowsUserName Property"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOMapping.WindowsUserName Property
The **WindowsUserName** property specifies the Microsoft Windows user name.  
  
 **Get** method:  
  
## Syntax  
  
```cpp#  
  
HRESULT ISSOMapping::get_WindowsUserName(BSTR*WindowsUserName);  
HRESULT ISSOMapping::put_WindowsUserName(BSTR WindowsUserName);  
```  
  
```vb  
  
Property WindowsUserName() As String  
```  
  
#### Parameters  
 `WindowsUserName`  
 [in] When putting the property, a string that contains the Windows user name. [out, retval] When getting the property, a string used to return the Windows user name.  
  
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
