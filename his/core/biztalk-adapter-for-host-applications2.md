---
title: "BizTalk Adapter for Host Applications2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 282496be-e6b3-4ced-ba02-5af3b2572d15
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# BizTalk Adapter for Host Applications
The Microsoft BizTalk Adapter for Host Applications is based on technology in Transaction Integrator (TI) that enables enterprises to connect BizTalk Server solutions to existing IBM mainframe zSeries (CICS and IMS) or midrange iSeries (RPG) server programs. The adapter offers an intuitive Visual Studio designer, including host COBOL and RPG source code import wizards, with which to generate XSD schemas for use in BizTalk projects. The administration tools are integrated with the BizTalk Server port configuration and deployment tools. Using this adapter, IT professionals can efficiently extend existing business rules in host programs with new solutions based on BizTalk Server 2006.  
  
> [!NOTE]
>  A receive location is not available for this adapter.  
  
 A typical scenario involves the following steps:  
  
- The IT professional installs the adapter.  
  
- The IT professional configures the adapter and uses Transaction Integrator to define the Remote Environment.  
  
- The developer creates the BizTalk application in Visual Studio. This involves defining the Remote Environment, building the TI assembly and schema, deploying, testing, and debugging the application, exporting the assemblies, and building the export package for use by BizTalk Server.  
  
- Finally, the IT professional imports the developer’s application into BizTalk Server, updates any necessary information, and deploys the application.  
  
  Tracing tools are available to debug your deployed application and improve its performance.  
  
  Some knowledge of Transaction Integrator is necessary. For an overview of TI basics, see the [Transaction Integrator User's Guide](../core/transaction-integrator-user-s-guide2.md).  
  
## In This Section  
 [How to Configure SSO for the Host Application Adapter](../core/how-to-configure-sso-for-the-host-application-adapter2.md)  
  
 [How to Create a Send Port for the Host Application Adapter](../core/how-to-create-a-send-port-for-the-host-application-adapter1.md)  
  
 [Creating an Application for the BizTalk Adapter for Host Applications](../core/creating-an-application-for-the-biztalk-adapter-for-host-applications2.md)  
  
 [How to Deploy the BizTalk Server Application](../core/how-to-deploy-the-biztalk-server-application2.md)  
  
## See Also  
 [Application Integration (Configuration)](../core/application-integration-configuration-2.md)