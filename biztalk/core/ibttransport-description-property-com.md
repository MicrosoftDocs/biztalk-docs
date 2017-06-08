---
title: "IBTTransport.Description Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33d68ae9-e67c-4f0f-8b5b-26dea7e8f46e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransport.Description Property (COM)
Gets the component description.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransport::get_Description(  
BSTR*  
Description  
);  
  
```  
  
```vb  
  
Property Description() As String  
  
```  
  
## Remarks  
 **Parameters**  
  
 *Description*  
 [out,retval] String used to return the description of the component.  
  
 None.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 Not applicable.  
  
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
 [IBTTransport Interface (COM)](../core/ibttransport-interface-com.md)   
 [IBTTransport Members (COM)](../core/ibttransport-members-com.md)