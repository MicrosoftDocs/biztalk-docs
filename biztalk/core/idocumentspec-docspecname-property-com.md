---
title: "IDocumentSpec.DocSpecName Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a21fdd1d-04ec-4a32-9d4f-2162c786cb66
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IDocumentSpec.DocSpecName Property (COM)
Gets the specification name of the current document.  
  
## Syntax  
  
```cpp  
  
HRESULT IDocumentSpec::get_DocSpecName(  
BSTR*  
DocSpecName  
);  
  
```  
  
```vb  
  
Property DocSpecName() As String  
  
```  
  
#### Parameters  
 *DocSpecName*  
 [out,retval] String used to return the schema name.  
  
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