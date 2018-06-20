---
title: "Before Installing the Service Oriented Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service solution tutorial, deployment prerequisites"
ms.assetid: 865bd21c-e49a-4647-af91-fefee07ee806
caps.latest.revision: 36
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Before Installing the Service Oriented Solution
The following prerequisites must be available to install the stub version of the service-oriented solution on a single computer:  
  
- [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].  
  
- Supported software for [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].  
  
- The latest version of IBM WebSphere MQ Client for Windows  
  
  > [!NOTE]
  >  MQSeries Server is not required for the stub version of the solution.  
  
  > [!NOTE]
  >  You can download IBM WebSphere MQ Client for Windows from the IBM Web site.  
  
  For installing the inline and adapter version of the service oriented solution on a single computer:  
  
- [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].  
  
  > [!NOTE]
  >  A domain account is required to map credentials for Enterprise Single Sign-On (SSO). We recommend using domain accounts for the BizTalk service and for the ENTSSO service accounts.  
  
- Supported software for [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].  
  
- MQSeries Server on the local computer or access to the computer running the MQSeries Server. For the inline version, MQSeries client APIs must be available on the BizTalk server running the solution’s orchestrations.  
  
  > [!NOTE]
  >  The version of MQSeries Server must match the version required by the BizTalk Server MQSeries Adapter. This can include IBM WebSphere MQ for Windows Version 5.3 with Fix Pack 10 (CSD10) or later.  
  
  > [!NOTE]
  >  When using features such as MQSeries which make Distributed Component Object Model (DCOM) calls to the server, make sure you do not have a Network Address Translation (NAT)-based firewall enabled. The client must be able to access the server by its actual IP address, and NAT-based firewalls translate this address to something the client will not recognize.  
  
- IBM Mainframe with CICS and Transaction X if you are using a variation of the solution that requires a mainframe. In this case, the CICS application (COBOL code) must be installed on the mainframe and Microsoft Host Integration Server (HIS) is required to access the mainframe.  
  
   If you don’t have a mainframe for the solution, you can modify the port binding to use the stub Web service for Pending Transactions. The Web service generates transactions locally to emulate the mainframe transactions. For more information about how to modify the port binding for the stub Pending Transactions Web service, see [How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md).  
  
- Host Integration Server is required to connect to the mainframe.  
  
  > [!NOTE]
  >  Host Integration Server is included as part of BizTalk Server.  
  
- Web server configured with a certificate for HTTPS connections.  
  
## See Also  
 [How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)   
 [How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)   
 [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md)   
 [Developer Machine Setup for the Service Oriented Solution](../core/developer-machine-setup-for-the-service-oriented-solution.md)