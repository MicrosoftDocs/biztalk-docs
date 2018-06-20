---
title: "Using the Exception Management Framework | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b69c9c01-e7e4-4788-8fe2-43d32075155d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the Exception Management Framework
The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses exceptions to communicate failures (for example, a non-deployed map or rules that do not return a map name) for dynamic transformations and routing. When a transformation or routing process fails, the ESB creates an exception message and submits it through a direct-bound port to the Message Box database. The ESB also implements a send port named ALL.Exceptions that subscribes to and retrieves exception messages and publishes them to the ESB Management Portal.  

 In addition, all orchestration samples use the ESB Failed Orchestration Exception Routing API to handle exceptions. You can use this API in any orchestration project you deploy. The ESB Failed Orchestration Exception Routing feature provides a standard way to trap and report all exceptions in a BizTalk Server environment.  

 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains several sample projects that demonstrate how to use the ESB Exception Management Framework. The following two projects encapsulate the ESB Failed Orchestration Exception Routing API:  

- **ESB.ExceptionHandling**. This project contains all the public methods for handling fault message processing in orchestrations. You must register the assembly in this project in the global assembly cache on the local server.  

- **ESB.ExceptionHandling.Schemas.Faults**. This project contains the fault message schema defined by the namespace **http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling** and the system property schema. You must deploy this project to the Microsoft.Practices.ESB application container.  

  All projects that use the ESB Failed Orchestration Exception Routing API must reference the core assemblies:  

- **Microsoft.Practices.ESB.ExceptionHandling.dll**  

- **Microsoft.Practices.ESB.ExceptionHandling.Schemas.Faults.dll**  

  The following sections provide more information about using the ESB Exception Management Framework:  

- [The ESB Exception API Members](../esb-toolkit/the-esb-exception-api-members.md)  

- [Creating and Publishing Fault Messages](../esb-toolkit/creating-and-publishing-fault-messages.md)  

- [Subscribing to and Extracting Messages](../esb-toolkit/subscribing-to-and-extracting-messages.md)  

- [Scenario Solution Steps](../esb-toolkit/scenario-solution-steps.md)
