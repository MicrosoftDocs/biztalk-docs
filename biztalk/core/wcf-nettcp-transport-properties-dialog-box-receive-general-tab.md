---
title: "WCF-NetTcp Transport Properties Dialog Box, Receive, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-nettcp.transport.receive.general"
helpviewer_keywords: 
  - "properties, WCF-NetTcp adapters"
  - "WCF-NetTcp adapters, properties"
ms.assetid: c43745ae-6b1b-43d5-8da0-34e2f8259e4f
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetTcp Transport Properties Dialog Box, Receive, General Tab
Use the **General** tab to configure the receive location for the WCF-NetTcp adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Address (URI)**|Required. Specify the fully qualified URI with the **net.tcp** scheme for this receive location.<br /><br /> Minimum length: 1<br /><br /> Maximum length: 255<br /><br /> Default value: net.tcp://localhost/|  
|**Endpoint Identity**|Optional. Specify the identity of the service that this receive location provides by clicking the **Edit** button. The values that can be specified for the **Endpoint Identity** property differ according to the security configuration. These settings enable the client to authenticate this receive location. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
  
## See Also  
 [The \<identity> element](http://go.microsoft.com/fwlink/?LinkID=75747)   
 [How to Configure a WCF-NetTcp Receive Location](../core/how-to-configure-a-wcf-nettcp-receive-location.md)   
 [Publishing Service Metadata for the WCF Receive Adapters](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)