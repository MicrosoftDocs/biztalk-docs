---
title: "IDocumentSpec.DocType Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec9331a5-1d05-4181-98e0-fe781cf74515
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IDocumentSpec.DocType Property (COM)
Gets the type of the document.  
  
## Syntax  
  
```cpp  
  
HRESULT IDocumentSpec::get_DocType(  
BSTR*  
DocType  
);  
  
```  
  
```vb  
  
Property DocType() As String  
  
```  
  
#### Parameters  
 *DocType*  
 [out,retval] String used to return the document type.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This property indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The property was successfully obtained or written.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IDocumentSpec Interface (COM)](../core/idocumentspec-interface-com.md)   
 [IDocumentSpec Members (COM)](../core/idocumentspec-members-com.md)   
 [Using the Parsing and Serializing Engines](../core/using-the-parsing-and-serializing-engines.md)