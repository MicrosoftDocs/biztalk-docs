---
title: "WCF-NetNamedPipe Transport Properties Dialog Box, Receive, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-netnamedpipe.transport.receive.general"
helpviewer_keywords: 
  - "properties, WCF-NetNamedPipe adapters"
  - "WCF-NetNamedPipe adapters, properties"
ms.assetid: 881b1fd1-6337-4026-baab-1de61594b95f
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetNamedPipe Transport Properties Dialog Box, Receive, General Tab
Use the **General** tab to configure the receive location for the WCF-NetNamedPipe adapter. The WCF-NetNamedPipe adapter provides efficient cross-process communication in a .NET-to-.NET environment. The adapter uses the named pipe transport and messages have a binary encoding. This adapter cannot be used in cross-computer communication.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Address (URI)**|Required. Specify the fully qualified URI with the **net.pipe** scheme for this receive location. For example, net.pipe://localhost/pipeName. **Note:**  The WCF-NetNamedPipe receive adapter does not use the computer name part in the URI to decide the pipe name. <br /><br /> Minimum length: 1<br /><br /> Maximum length: 255<br /><br /> Default value: net.pipe://localhost/|  
|**Endpoint Identity**|Optional. Specify the identity of the service that this receive location provides by clicking the **Edit** button. The values that can be specified for the **Endpoint Identity** property differ according to the security configuration. These settings enable the client to authenticate this receive location. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
  
## See Also  
 [How to Configure a WCF-NetNamedPipe Receive Location](../core/how-to-configure-a-wcf-netnamedpipe-receive-location.md)   
 [The \<identity> element](http://go.microsoft.com/fwlink/?LinkID=75747)   
 [Publishing Service Metadata for the WCF Receive Adapters](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)