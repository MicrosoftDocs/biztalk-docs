---
title: "IPipelineContext.GetGroupSigningCertificate Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dee7be36-2968-44a5-a76a-5d565d7e71dd
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IPipelineContext.GetGroupSigningCertificate Method (COM)
Get access to the helper interface to work with BizTalk Server message objects.  
  
## Syntax  
  
```cpp  
  
HRESULT IPipelineContext::GetGroupSigningCertificate(  
BSTR**  
ppRet  
);  
  
```  
  
```vb  
  
Function GetGroupSigningCertificate() As String  
  
```  
  
#### Parameters  
 *ppRet*  
 [out,retval] Pointer to hold the reference to the returned **String** containing the signing certificate for the group.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns the [IBaseMessageFactory](../core/ibasemessagefactory-interface-com.md) associated with the pipeline context.  
  
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
 [IPipelineContext Interface (COM)](../core/ipipelinecontext-interface-com.md)   
 [IPipelineContext Members (COM)](../core/ipipelinecontext-members-com.md)