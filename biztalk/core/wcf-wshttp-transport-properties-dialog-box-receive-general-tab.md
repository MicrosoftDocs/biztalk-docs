---
title: "WCF-WSHttp Transport Properties Dialog Box, Receive, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-wshttp.transport.receive.general"
helpviewer_keywords: 
  - "WCF-WSHttp adapters, properties"
  - "properties, WCF-WSHttp adapters"
ms.assetid: 530dd7e7-a610-4171-a3b0-06b7dd194a8a
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-WSHttp Transport Properties Dialog Box, Receive, General Tab
Use the **General** tab to configure the receive location for the WCF-WSHttp adapter.  
  
> [!NOTE]
>  If you use **Transport** or **TransportWithMessageCredential** for the **Security mode**, you must set up Secure Sockets Layer (SSL) in Microsoft Internet Information Services (IIS).  
  
|Use this|To do this|  
|--------------|----------------|  
|**Address (URI)**|Required. Specify the URI for this receive location. Specify the virtual directory plus the .svc file name that the BizTalk WCF Service Publishing Wizard generates—for example, /path/service.svc.<br /><br /> Default value: /<br /><br /> Minimum length: 1<br /><br /> Maximum length: 255|  
|**Endpoint Identity**|Optional. Specify the identity of the service that this receive location provides by clicking the **Edit** button. The values that can be specified for the **Endpoint Identity** property differ according to the security configuration. These settings enable the client to authenticate this receive location. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> The default is an empty string.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767|  
  
## See Also  
 [The \<identity> element](http://go.microsoft.com/fwlink/?LinkID=75747)   
 [How to Configure a WCF-WSHttp Receive Location](../core/how-to-configure-a-wcf-wshttp-receive-location.md)   
 [Publishing WCF Services with the Isolated WCF Receive Adapters](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)   
 [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)