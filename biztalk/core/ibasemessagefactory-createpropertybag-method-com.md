---
title: "IBaseMessageFactory.CreatePropertyBag Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8861750-ae0d-4076-9e24-92fd0ed8e732
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessageFactory.CreatePropertyBag Method (COM)
Creates a property bag for BizTalk message part.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessageFactory::CreatePropertyBag(  
IBasePropertyBag**  
ppPropBag  
);  
  
```  
  
```vb  
  
Function CreatePropertyBag() As IBasePropertyBag  
  
```  
  
#### Parameters  
 *ppPropBag*  
 [out,retval] Pointer to hold the reference to the returned **IBasePropertyBag** object/interface, which will contain the property bag.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns the **IBasePropertyBag** containing the context properties of the message.  
  
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