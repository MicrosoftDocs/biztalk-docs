---
title: "IDocumentSpec.GetSchemaCollection Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcc0f179-89c7-455c-996c-be9fb9590d02
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IDocumentSpec.GetSchemaCollection Method (COM)
Gets the schema collection.  
  
## Syntax  
  
```cpp  
  
HRESULT IDocumentSpec::GetSchemaCollection(  
IUnknown**  
ppRet  
);  
  
```  
  
```vb  
  
Function GetSchemaCollection() As IUnknown  
  
```  
  
#### Parameters  
 *ppRet*  
 [out,retval] Address of a pointer to receive an **IUnknown** interface, which will contain the XML schema collection that contains the schema collection.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns a **IUnknown** that contains the transaction that the Messaging Engine will use in agent interactions. This parameter may be **NULL**.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
  
## Remarks  
 The BizTalk Server Messaging Engine calls this method prior to pushing messages into the batch.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IDocumentSpec Interface (COM)](../core/idocumentspec-interface-com.md)   
 [IDocumentSpec Members (COM)](../core/idocumentspec-members-com.md)