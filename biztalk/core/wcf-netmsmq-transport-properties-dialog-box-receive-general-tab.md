---
title: "WCF-NetMsmq Transport Properties Dialog Box, Receive, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-netmsmq.transport.receive.general"
helpviewer_keywords: 
  - "WCF-NetMsmq adapters, properties"
  - "properties, WCF-NetMsmq adapters"
ms.assetid: 4059915a-9a01-4b64-8349-4c4864bcb5d6
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetMsmq Transport Properties Dialog Box, Receive, General Tab
Use the **Address** tab to configure the receive location for the WCF-NetMsmq adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Address (URI)**|Required. Specify the fully qualified URI with the **net.msmq** scheme for this receive location. For example, net.msmq://localhost/private/queueName. In addition, a public or private queue corresponding to the queue name in this address must be created before enabling this receive location. **Note:**  If you use a private queue for this receive location, you cannot receive from a remote client. **Note:**  If the WCF-NetMsmq receive adapter is running on Windows Vista, you can use subqueues included in Message Queuing (MSMQ) 4.0. Subqueues can be addressed as: net.msmq*://\<computer-name>*/applicationQueue;subqueueName, where *computer name* is the name of the computer on which the queue resides and the applicationQueue is the name of the application-specific queue. For more information about subqueues included in MSMQ 4.0, see related topic in See Also section of this topic. <br /><br /> Minimum length: 1<br /><br /> Maximum length: 255<br /><br /> Default value: net.msmq://localhost/|  
|**Endpoint Identity**|Optional. Specify the identity of the service that this receive location provides by clicking the **Edit** button. The values that can be specified for the **Endpoint Identity** property differ according to the security configuration. These settings enable the client to authenticate this receive location. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
  
## See Also  
 [Subqueues](http://go.microsoft.com/fwlink/?LinkId=83344)   
 [Public and private queues](http://go.microsoft.com/fwlink/?LinkId=75825)   
 [How to Configure a WCF-NetMsmq Receive Location](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)   
 [Publishing Service Metadata for the WCF Receive Adapters](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)