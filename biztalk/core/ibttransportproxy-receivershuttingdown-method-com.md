---
title: "IBTTransportProxy.ReceiverShuttingdown Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 767e6a3a-bbd2-4c02-81bb-3b3ff5faa0be
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportProxy.ReceiverShuttingdown Method (COM)
Notifies the BizTalk Server Messaging Engine that the receiver adapter is shutting down one of its receive locations.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTTransportProxy::ReceiverShuttingdown(  
        BSTR  
        bstrReceiveURL,  
HRESULTpErrorInfo);  
```  
  
```vb  
  
        Sub ReceiverShuttingdown(  
        bstrReceiveURL  
         As String,  
pErrorInfo As HRESULT)  
```  
  
## Remarks  
 **Parameters**  
  
 *bstrReceiveURL*  
 [in] String that contains the receive URL that is shutting down.  
  
 *bstrReceiveURL*  
 **String** that contains the receive URL that is shutting down.  
  
 *pErrorInfo*  
 [in] The error that is causing the URL to shut down.  
  
 *pErrorInfo*  
 The error that is causing the URL to shut down.  
  
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
  
 A receiver adapter can use this method to shutdown a receive endpoint or URL.  
  
 The receive endpoint will not be enabled automatically when service is restarted.  
  
 The adapter should not submit any new work after this method has been called.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportProxy Interface (COM)](../core/ibttransportproxy-interface-com.md)   
 [IBTTransportProxy Members (COM)](../core/ibttransportproxy-members-com.md)