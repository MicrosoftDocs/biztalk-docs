---
title: "IDocumentSpec.GetBodyPath Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31bb56aa-2f8e-44fe-a046-8d572d32198c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IDocumentSpec.GetBodyPath Method (COM)
Returns the XML Path (XPath) to the node in the document where the body part begins.  
  
## Syntax  
  
```cpp  
  
HRESULT IDocumentSpec::GetBodyPath(  
BSTR*  
pBodyPath  
);  
  
```  
  
```vb  
  
Function GetBodyPath() As String  
  
```  
  
#### Parameters  
 *pBodyPath*  
 [out,retval] For an envelope schema, this method returns the XPath to the node in the document where the body part begins. For a document schema, this method returns **null**.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 For an envelope schema, this property contains the XPath to the node in the document where the body part begins. For a schema, this property will be **Null**.  
  
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
 [IDocumentSpec Interface (COM)](../core/idocumentspec-interface-com.md)   
 [IDocumentSpec Members (COM)](../core/idocumentspec-members-com.md)   
 [Using the Parsing and Serializing Engines](../core/using-the-parsing-and-serializing-engines.md)