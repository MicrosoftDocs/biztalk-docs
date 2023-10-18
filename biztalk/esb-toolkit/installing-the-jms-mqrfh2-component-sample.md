---
description: "Learn more about: Installing the JMS MQRFH2 Component Sample"
title: "Installing the JMS MQRFH2 Component Sample"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Installing the JMS MQRFH2 Component Sample
To use this sample with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], you must also install the following:

- IBM WebSphere MQ 5.3 (with CSD12), WebSphere MQ 6.x or WebSphere MQ 7.0

- The IBM "RfhUtil" JMS test utility for queuing and retrieving messages

  The JMS MQRFH2 Component sample requires the JMS MQRFH2 component to reside in the PipelineComponents folder of your Microsoft BizTalk Server installation folder and the corresponding schemas to reside in the global assembly cache. Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core automatically copies and installs the assemblies to the correct locations. However, if required, you can manually perform these tasks.

  **To manually install the JMS MQRFH2 component and schemas**

1. Copy the assembly Microsoft.Practices.ESB.JMS.PipelineComponents.dll to the PipelineComponents folder of your BizTalk Server installation folder.

2. Add the schema assembly Microsoft.Practices.ESB.JMS.Schemas.Property.dll to the global assembly cache using the .NET Framework Configuration Tool located in the Administrative Tools section of the **Start** menu.

   This section describes the process for installing the JMS MQRFH2 sample into the GlobalBank.JMS BizTalk application. Before you install this sample, you must install the ESB Toolkit Core as described in [Install and configure the Microsoft BizTalk ESB Toolkit](/biztalk/esb-toolkit/install-and-configure-the-microsoft-biztalk-esb-toolkit).

   You can install the JMS MQRFH2 Component sample from the solution project or use the Windows Installer file included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. This section contains the following topics:

-   [Install the JMS MQRFH2 Sample Using the Install Scripts](../esb-toolkit/install-the-jms-mqrfh2-sample-using-the-install-scripts.md)

-   [Assemblies and Artifacts Installed by the JMS MQRFH2 Component Sample](../esb-toolkit/assemblies-and-artifacts-installed-by-the-jms-mqrfh2-component-sample.md)

-   [Test the JMS MQRFH2 Sample Installation](../esb-toolkit/test-the-jms-mqrfh2-sample-installation.md)
