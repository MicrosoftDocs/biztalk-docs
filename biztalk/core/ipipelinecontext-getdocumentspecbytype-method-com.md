---
title: "IPipelineContext.GetDocumentSpecByType Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34d689c9-6dd7-48c0-a41d-a63730fc0e1c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IPipelineContext.GetDocumentSpecByType Method (COM)
Gets the [IDocumentSpec](../core/idocumentspec-interface-com.md) object for specified document type.  
  
## Syntax  
  
```cpp  
  
        HRESULT IPipelineContext::GetDocumentSpecByType(  
        BSTR  
        DocType,  
IDocumentSpec**ppRet);  
```  
  
```vb  
  
Function GetDocumentSpecByType(  
DocType  
 As String  
) As IDocumentSpec  
  
```  
  
#### Parameters  
 *DocType*  
 [in] String that contains the document type.  
  
 *DocType*  
 **String** that contains the document type.  
  
 *ppRet*  
 [out,retval] Pointer to hold the reference to the returned **IDocumentSpec** object/interface.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it the **IDocumentSpec** containing the document with the specified type.  
  
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