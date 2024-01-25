---
description: "Learn more about: Installing and Configuring BizTalk Accelerator for SWIFT on Orchestration Servers"
title: "Installing and Configuring BizTalk Accelerator for SWIFT on Orchestration Servers"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Installing and Configuring BizTalk Accelerator for SWIFT on Orchestration Servers
This section describes how to install and configure [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] on the orchestration servers. These servers are mainly used to run the FIN Repair and Reconciliation orchestration and the Message Repair/New Submission orchestration.  

### To install and configure BizTalk Accelerator for SWIFT on the orchestration server  

1. Perform a Custom Install of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]. Install the **MRSR** feature.  

   > [!NOTE]
   >  You do not need to install the Web Components for Message Repair and New Submission feature because this server does not have MRSR site.  

   > [!NOTE]
   >  After installation is complete, the Configuration Wizard starts.  

2. In the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, configure **MCRR**.
