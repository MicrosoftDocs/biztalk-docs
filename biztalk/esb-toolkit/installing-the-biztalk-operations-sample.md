---
title: "Installing the BizTalk Operations Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57c982c2-f796-4c63-9bca-7e8965779850
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing the BizTalk Operations Sample
The Microsoft BizTalk Operations sample requires the ESB BizTalk Operations service installed and configured. ESB BizTalk Operations service is one of the core Web services that can be installed and configured using the ESB Configuration Tool. For more information about using the ESB Configuration Tool, see [http://msdn.microsoft.com/library/jj684558(v=bts.80).aspx](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx). The default location of the BizTalk Operations Web service is <http://localhost/ESB.BizTalkOperationsService/Operations.asmx>; however, you can change this in the application configuration file if you deploy the service in a different location or a remote server.  

 You must install BizTalk Operations sample from the solution project.  

 **To install the BizTalk Operations sample**  

1. Open the solution named ESB.BizTalkOperations.Test.Client.csproj from the \Source\Samples\BizTalkOperations folder where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples into Visual Studio.  

2. Use the commands on the **Build** menu to compile the solution.
