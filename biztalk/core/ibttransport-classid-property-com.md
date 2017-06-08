---
title: "IBTTransport.ClassID Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3de411ae-57e4-4af3-994d-0e8d26d735bf
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransport.ClassID Property (COM)
Gets the class ID of the adapter, a globally unique identifier (GUID) that identifies the adapter.  
  
```cpp  
  
ClassID  
  
```  
  
```vb  
  
GUID  
```  
  
## Remarks  
 **Parameters**  
  
 *ClassID*  
 [out, retval] Globally unique identifier (GUID) used to return the class ID of the adapter.  
  
 None.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 Not applicable.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This property indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The property was successfully obtained or written.|  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransport Interface (COM)](../core/ibttransport-interface-com.md)   
 [IBTTransport Members (COM)](../core/ibttransport-members-com.md)