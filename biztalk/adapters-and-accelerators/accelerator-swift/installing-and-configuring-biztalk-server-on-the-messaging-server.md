---
description: "Learn more about: Installing and Configuring BizTalk Server on the Messaging Server"
title: "Installing and Configuring BizTalk Server on the Messaging Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Installing and Configuring BizTalk Server on the Messaging Server
This section describes how to install and configure BizTalk Server to be used as the messaging server for connecting to the SWIFT network.

### To install and configure BizTalk Server on the Messaging Server

1. Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing all the features except EDI, Human Workflow Services (HWS), and MRSR site, unless required by other applications.

   > [!NOTE]
   >  Note that in single-computer deployment, this computer is the same computer as the one that runs the HTTP front-end service.

2. Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].

   > [!NOTE]
   >  Do not install Message Queuing, because we will be installing the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] version of MSMQ known as MSMQT. For more information about MSMQT, see BizTalk Message Queuing Adapter (MSMQT) Configuration on the MSDN Web site at [https://go.microsoft.com/fwlink/?LinkID=48875](https://go.microsoft.com/fwlink/?LinkID=48875).

3. Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide. At the time of this publication, there are no required hotfixes.
