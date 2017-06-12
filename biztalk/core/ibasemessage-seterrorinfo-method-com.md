---
title: "IBaseMessage.SetErrorInfo Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f84ec341-bff7-4f00-af8e-a9100ab986c5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.SetErrorInfo Method (COM)
Sets the error information.  
  
## Syntax  
  
```cpp  
  
          HRESULT IErrorInfo::SetErrorInfo(   
IErrorInfo pErrInfo);  
```  
  
```vb  
  
Sub SetErrorInfo(  
pErrInfo  
As IErrorInfo)  
  
```  
  
#### Parameters  
 *pErrInfo*  
 [in] The error information.  
  
 *pErrInfo*  
 [in] The error information.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)   
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)