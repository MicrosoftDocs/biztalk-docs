---
title: "IBTTransportProxy.TerminateIsolatedReceive Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a894785-8bb0-4a5f-afab-b85cc18ced67
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportProxy.TerminateIsolatedReceive Method (COM)
Notifies the Messaging Engine that it is shutting down. This method is called by a non-creatable receiver.  
  
## Syntax  
  
```cpp  
  
HRESULT IBTTransportProxy::TerminateIsolatedReceiver();  
  
```  
  
```vb  
  
Sub TerminateIsolatedReceiver()  
  
```  
  
## Remarks  
 **Return Values**  
  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
 **Error Values**  
  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
  
 **Remarks**  
  
 The **TerminateIsolatedReceiver** method should be called after all [RegisterIsolatedReceiver](../core/ibttransportproxy-registerisolatedreceiver-method-com.md) method calls, the process will hang on exit if this is not done.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportProxy Interface (COM)](../core/ibttransportproxy-interface-com.md)   
 [IBTTransportProxy Members (COM)](../core/ibttransportproxy-members-com.md)