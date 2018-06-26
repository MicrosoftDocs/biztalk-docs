---
title: "Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Accelerator for SWIFT, configuring"
  - "BizTalk Accelerator for SWIFT, installing on Messaging servers"
  - "BizTalk Messaging servers, installing BizTalk Accelerator for SWIFT"
ms.assetid: 7a8f60aa-5ff2-4584-9d4a-dc4a0ba61aca
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers
This section describes how to install and configure [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] on the messaging servers. These servers are mainly used to communicate with the SWIFT Network.  

### To install and configure BizTalk Accelerator for A4SWIFT on the Messaging Server  

1. Perform a Custom Install of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]. Install the **MRSR** and **SWIFT Messages** features.  

   > [!NOTE]
   >  You do not need to install the Web Components for Message Repair and New Submission feature because this server does not have MRSR site.  

   > [!NOTE]
   >  After installation is complete, the Configuration Wizard starts.  

2. In the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, configure **MCRR**.
