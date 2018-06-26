---
title: "Installing and Configuring BizTalk Server on the HTTP Front-End Servers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP server, installing BizTalk Server"
  - "BizTalk Server, installing on HTTP servers"
ms.assetid: dc1b3675-483a-478f-b30d-62efb73ad13c
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing and Configuring BizTalk Server on the HTTP Front-End Servers
This section describes how to install and configure BizTalk Server to be used as the HTTP front-end server for hosting the MRSR site and the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] template forms.  

### To install and configure BizTalk Server on the BizTalk HTTP front-end servers  

1. Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing the following features: **Business Rules Engine** and **SharePoint Adapter**.  

   > [!NOTE]
   >  Other features are not required for this installation.  

   > [!NOTE]
   >  On one of the BizTalk HTTP front-end servers, when you perform configuration, create the BizTalk Group.  

2. Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  

3. Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide.
