---
title: "IBTTransportProxy.SetErrorInfo Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f05983ae-1c10-4724-9aa0-17de892730a6
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportProxy.SetErrorInfo Method (COM)
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
  
## Remarks  
 **Parameters**  
  
 *pErrInfo*  
 [in] The error information.  
  
 *pErrInfo*  
 [in] The error information.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportProxy Interface (COM)](../core/ibttransportproxy-interface-com.md)   
 [IBTTransportProxy Members (COM)](../core/ibttransportproxy-members-com.md)