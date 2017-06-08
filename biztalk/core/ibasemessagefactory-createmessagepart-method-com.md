---
title: "IBaseMessageFactory.CreateMessagePart Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e9e0d87-2800-4f2d-a907-171c9ac4afad
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessageFactory.CreateMessagePart Method (COM)
Creates a BizTalk message part.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessageFactory::CreateMessagePart(  
IBaseMessagePart**  
ppPart  
);  
  
```  
  
```vb  
  
Function CreateMessagePart() As IBaseMessagePart  
  
```  
  
#### Parameters  
 *ppPart*  
 [out,retval] Pointer to hold the reference to the returned **IBaseMessagePart** object/interface, which will contain the part.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns the **IBaseMessagePart** containing the message part.  
  
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
 [IBaseMessageFactory Interface (COM)](../core/ibasemessagefactory-interface-com.md)   
 [IBaseMessageFactory Members (COM)](../core/ibasemessagefactory-members-com.md)