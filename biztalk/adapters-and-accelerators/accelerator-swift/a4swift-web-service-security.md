---
title: "A4SWIFT Web Service Security | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IIS security"
  - "Web service [A4SWIFT]"
  - "security, transport-level security"
  - "security, message-level security"
  - "ASP.NET security"
  - "A4SWIFT, Web service"
  - "A4SWIFT, security"
  - "security, IIS"
  - "security, ASP.NET"
  - "security, Web service"
  - "messages, security"
ms.assetid: e6c7d275-569f-47f6-81fb-10bcd86ff417
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# A4SWIFT Web Service Security
The [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]Web service by default is installed in a highly secure hybrid security model. In the IIS/ASP.NET model a trust boundary exists between the Web service, the [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] site, and the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]database.  
  
## IIS and ASP.NET Security Settings  
 When a call is made to the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Web server, IIS first authenticates the user by using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication. The web.config Web service is set by default to use [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication without impersonation, and validates that the caller is a member of the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Users group. If the caller is a member of the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Users group, the Web service methods are run under the process identity of the application pool. For [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], this is the default application pool for [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)].  
  
 For the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Web service to delete the message from the inbox of the Web method caller, the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Web service must impersonate the caller for the **Delete** and **GetCheckedOutUser** methods. These are the only methods run under the context of the original caller. Because the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Web service is impersonating the caller of these Web methods, the caller must have explicit permissions set on the SharePoint document libraries upon which the caller is acting.  
  
## A4SWIFT Secure Communication Settings  
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] is concerned with guaranteeing the integrity and confidentiality of Web service messages as they flow from [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] to [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] to BizTalk applications across the network. To provide the highest level of security [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] supports two levels of secure communication between applications: transport-level and message-level.  
  
## Transport-Level Security  
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] supports SSL communication between [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Web service, [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] automatically adapts to the MRSR site security settings when transmitting messages.  
  
 Internet Protocol security (IPSec) can also be implemented to secure communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].  
  
 For more information about implementing IPSec for secure communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], see "Securing Your Deployment of BizTalk Server" in BizTalk Server Help.  
  
  
## Message-Level Security  
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] message-level security is achieved by digitally signing messages to provide integrity. Message signing in [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] is covered in detail in [InfoPath Security](../../adapters-and-accelerators/accelerator-swift/infopath-security.md).