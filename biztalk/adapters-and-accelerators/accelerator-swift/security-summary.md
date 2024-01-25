---
description: "Learn more about: Security Summary"
title: "Security Summary"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Security Summary
## Overview
Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides development and runtime components to facilitate BizTalk applications that provide SWIFT messaging and automation functionality. Applications developed by using [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] are BizTalk applications and are secured by native [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], and IIS/ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] security features.

 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] protects privacy of system elements by using de facto Internet encrypted communications standards and protocols. Communication participants, processes, and information are secured by using signing certificates, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and Enterprise Single Sign-On. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] also enforces authorization of resource usage with mechanisms such as [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] Roles and [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and the MessageBox database.

 In addition to native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features, [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] defines and enforces security semantics for the creation, repair, approval, and submission of SWIFT messages by business users. This user-level security is enforced by using [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] digital signing technologies on the user workstation, and certificate and data integrity verification by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] runtime services on the server.

 Together, [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provide the platform, infrastructure, and tools for designing, developing, and executing secure SWIFT messaging and workflow automation systems.

## More information
For information about security best practices, see the following resources:


- Symantec security guide showing how to use their tools to implement the best practices described in [Microsoft Security Operations Guide for [!INCLUDE[btsWin2kSvr](../../includes/btswin2ksvr-md.md)]](https://go.microsoft.com/fwlink/p/?LinkId=28274).


- [Microsoft Security Notification Service](https://www.microsoft.com/msrc/technical-security-notifications)


## See Also
[Runtime, message repair, FIN response, and messaging](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)
