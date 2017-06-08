---
title: "IBTTransportProxy.GetMessageFactory Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce8dff51-a7b6-459c-a770-e5c29430970f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportProxy.GetMessageFactory Method (COM)
Gets the base message factory.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportProxy::GetMessageFactory(  
IBaseMessageFactory**  
ppRet  
);  
  
```  
  
```vb  
  
Function GetMessageFactory() As IBaseMessageFactory  
  
```  
  
## Remarks  
 **Parameters**  
  
 *ppRet*  
 [out,retval] Pointer to hold the reference to the returned **IBaseMessageFactory** object/interface for the message factory.  
  
 None.  
  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns an `IBaseMessageFactory` for the message factory.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
 **Remarks**  
  
 The adapter should use the message factory to create messages.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportProxy Interface (COM)](../core/ibttransportproxy-interface-com.md)   
 [IBTTransportProxy Members (COM)](../core/ibttransportproxy-members-com.md)