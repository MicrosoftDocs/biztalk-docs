---
title: "ISSOMapper.SetWindowsPassword Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d02c4959-4c6e-4f94-945f-1451bc78c5de
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
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
 [ISSOMapper Interface (COM)](../core/issomapper-interface-com.md)   
 [ISSOMapper Members](../core/issomapper-members.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)