---
description: "Learn more about: Installing the BizTalk Operations Sample"
title: "Installing the BizTalk Operations Sample"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Installing the BizTalk Operations Sample

The Microsoft BizTalk Operations sample requires the ESB BizTalk Operations service installed and configured. ESB BizTalk Operations service is one of the core Web services that can be installed and configured using the ESB Configuration Tool. For more information, go to [Install and configure the Microsoft BizTalk ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md).

The default location of the BizTalk Operations Web service is `http://localhost/ESB.BizTalkOperationsService/Operations.asmx`. However, you can change this in the application configuration file if you deploy the service in a different location or a remote server.  

 You must install BizTalk Operations sample from the solution project.  

 **To install the BizTalk Operations sample**  

1. Open the solution named ESB.BizTalkOperations.Test.Client.csproj from the \Source\Samples\BizTalkOperations folder where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples into Visual Studio.  

2. Use the commands on the **Build** menu to compile the solution.
