---
title: "IBTTransport.TransportType Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d676d74-89dd-41ed-8ee3-81e9f34fa88e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransport.TransportType Property (COM)
Gets the transport type of an adapter, such as FILE, HTTP, SMTP, or SOAP.  
  
```cpp  
  
TransportType  
  
```  
  
```vb  
  
```  
  
## Remarks  
 **Parameters**  
  
 *TransportType*  
 [out,retval] String used to return the name of the protocol implemented by the adapter.  
  
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