---
title: "Configuring the WCF Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NetTcpBinding [WCF adapters]"
  - "configuring [WCF adapters]"
  - "WCF adapters, pre-defined bindings"
  - "configuring [WCF adapters], about configuring WCF adapters"
  - "WsHttpBinding [WCF adapters]"
  - "BasicHttpBinding [WCF adapters]"
  - "NetNamedPipeBinding [WCF adapters]"
  - "NetMsmqBinding [WCF adapters]"
  - "bindings, pre-defined [WCF adapters]"
  - "WCF adapters, configuring"
ms.assetid: af01e2d4-303d-407a-b853-dd90b0246a8a
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring the WCF Adapters
The BizTalk Adapters for Windows Communication Foundation (WCF) allow  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to communicate with WCF-based applications. The BizTalk WCF adapters include five physical adapters that represent the WCF predefined bindings—**BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, and **NetMsmqBinding**. The WCF adapters for the predefined bindings are provided to enable you to easily configure necessary information for most application requirements.  
  
 The BizTalk WCF adapters also include two adapters that enable you to freely configure WCF binding and behavior information for the receive location and send port.  
  
 All the WCF adapters provide similar transport properties dialog boxes for send ports and receive locations. However, the detailed tasks to configure the WCF adapters vary depending on the physical adapter. Tasks not directly related to the adapter bindings, such as installing certificates, are the same for all the WCF adapters. This section discusses the tasks that are common to all the WCF adapters. For information about tasks that differ for each adapter, see the appropriate topics for the adapter in [WCF Adapters](../core/wcf-adapters.md).  
  
## In This Section  
  
-   [WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md)  
  
-   [WCF Adapters Security Recommendations](../core/wcf-adapters-security-recommendations.md)  
  
-   [Installing Certificates for the WCF Adapters](../core/installing-certificates-for-the-wcf-adapters.md)  
  
-   [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [How to Enable the WCF Extensibility Points with the WCF Adapters](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)  
  
-   [WCF Adapters Performance Counters](../core/wcf-adapters-performance-counters.md)  
  
-   [Single Sign-On Support for the WCF Adapters](../core/single-sign-on-support-for-the-wcf-adapters.md)  
  
## See Also  
 [WCF Adapters](../core/wcf-adapters.md)