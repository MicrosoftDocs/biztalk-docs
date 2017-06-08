---
title: "IBTTransportBatch.ResourceTracker Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d175ff6-7582-48fe-8707-6eb59a2d61eb
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch.ResourceTracker Property (COM)
This property is not supported and returns a value of E_NOTIMPL.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportBatch::IResourceTracker(  
ResourceTracker  
resourceTracker  
);  
  
```  
  
```vb  
  
Property ResourceTracker() As IResourceTracker  
  
```  
  
## Remarks  
 **Parameters**  
  
 *bstrCorrelationToken*  
 [out,retval] Not implemented.  
  
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
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)   
 [IBTTransportBatch Members (COM)](../core/ibttransportbatch-members-com.md)