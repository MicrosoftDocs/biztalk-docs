---
title: "IBaseMessage.GetErrorInfo Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b68d601-fafb-4604-b1c3-171ab6072d66
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.GetErrorInfo Method (COM)
Gets the exception that caused the error.  
  
## Syntax  
  
```cpp  
  
HRESULT IErrorInfo::GetErrorInfo(  
);  
  
```  
  
```vb  
  
Function GetErrorInfo(  
) As IErrorInfo  
  
```  
  
#### Parameters  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Requirements  
 **Platforms:** [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)   
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)