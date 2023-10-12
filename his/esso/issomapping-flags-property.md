---
description: "Learn more about: ISSOMapping.Flags Property"
title: "ISSOMapping.Flags Property"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOMapping.Flags Property
The **Flags** property is reserved for internal use only.  
  
## Syntax  
  
```cpp  
  
HRESULT ISSOMapping::get_Flags(BSTR* Flags);  
HRESULT ISSOMapping::put_Flags(BSTR Flags);  
  
```  
  
```vb  
  
Property Flags() As String  
  
```  
  
#### Parameters  
 `Flags`  
 [in] When putting the property, a string that contains the flag value. [out, retval] When getting the property, a string used to return the flag value.  
  
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
