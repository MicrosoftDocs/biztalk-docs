---
title: "Installing and Configuring BizTalk Accelerator for SWIFT on HTTP Front-End Servers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP server, installing BizTalk Accelerator for SWIFT"
  - "BizTalk Accelerator for SWIFT, installing on HTTP server"
ms.assetid: 1deaa5f7-9da2-4d4b-8367-2d6900065839
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing and Configuring BizTalk Accelerator for SWIFT on HTTP Front-End Servers
This section describes how to install and configure [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] on the HTTP front-end servers. These servers are mainly used to communicate with the SWIFT Network.  

### To install and configure BizTalk Accelerator for SWIFT on the HTTP front-end server  

1. Perform a Custom Install of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]. Install the **MRSR** and **Web Components for Message Repair and New Submission** features.  

   > [!NOTE]
   >  After installation is complete, the Configuration Wizard starts.  

2. In the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, configure **MCRR** and **WebService**.  

3. After completing the Configuration Wizard, on the Web servers, open the web.config file in the folder \<*Drive*\>:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\Service\ in Notepad. Search for "Authorization". In the **Authorization** section, set the roles value to the name of the A4SWIFT users group.
