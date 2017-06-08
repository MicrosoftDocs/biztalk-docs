---
title: "IPipelineContext.GetDocumentSpecByName Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5bdf0e8f-32bb-4bef-8245-3b9518cd182a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IPipelineContext.GetDocumentSpecByName Method (COM)
Gets the [IDocumentSpec](../core/idocumentspec-interface-com.md) object for the specified document name.  
  
## Syntax  
  
```cpp  
  
        HRESULT IPipelineContext::GetDocumentSpecByName(  
        BSTR  
        DocSpecName,  
IDocumentSpec**ppRet);  
```  
  
```vb  
  
Function GetDocumentSpecByName(  
DocSpecName  
 As String  
) As IDocumentSpec  
  
```  
  
#### Parameters  
 *DocSpecName*  
 [in] String that contains the schema name.  
  
 *DocSpecName*  
 **String** that contains the schema name.  
  
 *ppRet*  
 [out,retval] Pointer to hold the reference to the returned **IDocumentSpec** object/interface.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns the **IDocumentSpec** containing the document with the specified name.  
  
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