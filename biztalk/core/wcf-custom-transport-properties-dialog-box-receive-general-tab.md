---
title: "WCF-Custom Transport Properties Dialog Box, Receive, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.transport.receive.general"
helpviewer_keywords: 
  - "WCF-Custom adapters, properties"
  - "properties, WCF-Custom adapters"
ms.assetid: eef3d8c6-f79e-49de-b6d4-0d5a41d4463f
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-Custom Transport Properties Dialog Box, Receive, General Tab
Use the **General** tab to configure the endpoint address, and the service identity for the WCF-Custom and WCF-CustomIsolated receive locations.  
  
 The WCF-Custom adapter enables the use of Windows Communication Foundation (WCF) extensibility features. The WCF-Custom receive adapter allows users to select and configure a WCF binding, behavior, and behavior extensions for the receive location running in an in-process host.  
  
 The WCF-CustomIsolated adapter enables the use of Windows Communication Foundation (WCF) extensibility features over the HTTP transport. The WCF-CustomIsolated adapter allows users to select and configure a WCF binding, behavior, and behavior extensions for the receive location running in an isolated host. To use the WCF-CustomIsolated adapter, you must create in Microsoft Internet Information Services (IIS) the virtual directory corresponding to this receive location by using the BizTalk WCF Service Publishing Wizard.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Address (URI)**|Required. If you use the WCF-Custom receive adapter, specify the fully qualified URI of the service that this receive location publishes. The available transport scheme for this property is determined by the **Binding Type** property on the **Binding** tab. If you use the WCF-CustomIsolated adapter, specify the URI for this receive location. Specify the virtual directory plus the .svc file name that the BizTalk WCF Service Publishing Wizard generates—for example, /path/service.svc. **Note:**  You can also import and export this property through the **Import/Export** tab. <br /><br /> Minimum length: 0<br /><br /> Maximum length: 255<br /><br /> The default is an empty string.|  
|**Endpoint Identity**|Optional. Specify the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the WCF infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the **Endpoint Identity** property differ according to the security configuration. **Note:**  You can also import and export this property through the **Import/Export** tab. If the receive location is configured to use multiple identity types, only the identity type with the lowest number can be exported. For example, if **1. DNS** and **4. RSA** are both set in the **Identity Editor** dialog box, only the **1. DNS** property is saved by using the **Export** tab. <br /><br /> The default value is an empty string.|  
  
## See Also  
 [How to Configure a WCF-Custom Receive Location](../core/how-to-configure-a-wcf-custom-receive-location.md)   
 [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)   
 [Publishing Service Metadata for the WCF Receive Adapters](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)   
 [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)   
 [Publishing WCF Services with the Isolated WCF Receive Adapters](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)   
 [The \<identity> element](http://go.microsoft.com/fwlink/?LinkID=75747)