---
title: "IBTTransportProxy.RegisterIsolatedReceiver Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 589f7158-8a05-4522-9bc2-07ba2f9b197c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportProxy.RegisterIsolatedReceiver Method (COM)
Registers an isolated receiver.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBTTransportProxy::RegisterIsolatedReceiver(  
        BSTR  
        bstrURL,  
IBTTransportConfig*pCallBack);  
```  
  
```vb  
  
        Sub RegisterIsolatedReceiver(  
        bstrURL  
         As String,  
pCallBack As IBTTransportConfig)  
```  
  
## Remarks  
 **Parameters**  
  
 *bstrURL*  
 [in] String that contains the URL that the adapter is listening on.  
  
 *bstrURL*  
 **String** that contains the URL that the adapter is listening on.  
  
 *pCallBack*  
 [in] Reference to a **IBTTransportConfig** object/interface that will be called back with the configuration of the *bstrURL* parameter.  
  
 *pCallBack*  
 **IBTTransportConfig** object/interface that will be called back with the configuration of the *bstrURL* parameter.  
  
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
  
 An ISAPI extension is an example of a non-creatable receive function because BizTalk Server does not have control over the lifetime of the ISAPI extension. In this scenario, the non-creatable adapter is responsible for creating the transport proxy and registering itself with the transport proxy.  
  
 The [TerminateIsolatedReceive](../core/ibttransportproxy-terminateisolatedreceive-method-com.md)method should be called after all **RegisterIsolatedReceiver** method calls, the process will hang on exit if this is not done.  
  
 **Requirements**  
  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTTransportProxy Interface (COM)](../core/ibttransportproxy-interface-com.md)   
 [IBTTransportProxy Members (COM)](../core/ibttransportproxy-members-com.md)