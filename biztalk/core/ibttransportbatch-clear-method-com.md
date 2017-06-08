---
title: "IBTTransportBatch.Clear Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f54feaa-86d2-4c69-87b7-c7a7e5d321fc
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.Clear Method (COM)
Clears the batch.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportBatch::Clear(  
);  
  
```  
  
```vb  
  
Sub Clear()  
  
```  
  
## Remarks  
 **Parameters**  
  
 None.  
  
 None.  
  
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
  
 **Remarks**  
  
 This method is implicitly called when the [Done](../core/ibttransportbatch-done-method-com.md) method is called.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)   
 [IBTTransportBatch Members (COM)](../core/ibttransportbatch-members-com.md)