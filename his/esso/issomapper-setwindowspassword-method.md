---
description: "Learn more about: ISSOMapper.SetWindowsPassword Method"
title: "ISSOMapper.SetWindowsPassword Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1fe0fc9-4eef-462a-96a9-b4f4a0ae9882
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# ISSOMapper.SetWindowsPassword Method
The **SetWindowsPassword** method sets the Microsoft Windows password. This method is not currently implemented.  
  
## Syntax  
  
```cpp#  
  
HRESULT SetWindowsPassword(  
BSTR bstrWindowsPassword  
);  
```  
  
```vb  
  
Sub SetWindowsPassword(  
bstrWindowsPassword As String  
)  
```  
  
#### Parameters  
 `bstrWindowsPassword`  
 [in]  String that specifies the Windows password.  
  
 `bstrWindowsPassword`  
 [in]  String that specifies the Windows password.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|E_NOTIMPL|The method is not implemented.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOMapper Interface (COM)](../esso/issomapper-interface-com.md)   
 [ISSOMapper Members](../esso/issomapper-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)
