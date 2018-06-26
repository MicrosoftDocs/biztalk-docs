---
title: "Supported Features2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a783f6c-10c4-4e57-b8ef-00622501dceb
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Supported Features
This topic lists the features that are supported over the IP-DLC link service.  
  
## Base SNA Features  
 The following existing [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] SNA features are supported over the IP-DLC link service:  
  
- LU types 0, 1, 2, 3 and 6.2 (dependent and independent)  
  
- LUA, FMI, APPC, and CPI-C APIs  
  
- Dynamically Defined Dependent LUs (DDDLUs)  
  
- Dynamic addition of local LUs, remote LUs, and connections  
  
- Incoming and outgoing calls  
  
- Connection Activation at Server startup, on demand or by administrator  
  
- SNA data compression  
  
- PU concentration with the upstream link over IP-DLC  
  
  Because the preceding SNA features are supported, it follows that the following applications are also supported over the IP-DLC link service:  
  
- [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]-compatible 3270 emulators  
  
- [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]-compatible 5250 emulators  
  
- APPC - 3270 Session Viewer (including the LU-LU Test feature)  
  
- Host Print Service  
  
- Data Integration Services (data providers for DB2 and host files)  
  
- Local and remote administration  
  
- TN3270 server  
  
- TN5250 server  
  
- Session Integrator  
  
- Message Integration (WCF Channel for WebSphere MQ)  
  
- Application Integration Transaction Integrator  
  
- BizTalk Adapters  
  
## Fault Tolerance Features  
 Note that because the IP-DLC link service uses the APPN and HPR/IP protocols, it is automatically able to take advantage of the following fault tolerance features:  
  
-   Ability to reroute sessions around a failure in the network provided that an alternative route exists.  
  
-   Ability for mainframe applications to be moved to a different processor with little or no impact to users when system or application failures occur on the mainframe.  
  
## Security Features  
 Because the IP-DLC link service uses UDP/IP, the Windows IPsec feature can be used to provide end-to-end data security over the IP-DLC link service. Windows handles configuration of IPsec independently. No specific configuration is required for the IP-DLC link service.  
  
## Diagnostic Features  
 The diagnostics provided by the IP-DLC link service are used through the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Tracer Initiator and Trace Viewer facilities.  
  
## See Also  
 [System Overview](../core/system-overview1.md)   
 [Scalability](../core/scalability1.md)   
 [Key Limitations](../core/key-limitations2.md)   
 [IP-DLC Link Service Concepts and Terminology](../core/ip-dlc-link-service-concepts-and-terminology1.md)