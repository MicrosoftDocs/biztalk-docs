---
title: "Assigning Rights | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "user accounts, assigning permissions"
  - "security, user accounts"
  - "document library, new messages"
  - "document library, unparsed"
  - "messages, document library"
  - "privileges"
  - "permissions"
  - "unparsed document library"
  - "security, permissions"
ms.assetid: cee44240-aa00-4080-9e7f-728b2421102b
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Assigning Rights
The following permissions should be granted on the Document libraries for each site group created in the preceding topic:  


|                                         Document library                                         |                                   Site groups                                   | Custom document library permissions to apply |
|--------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|----------------------------------------------|
|                                    Templates document library                                    | Payments_Creators<br /><br /> Payments_Repairers<br /><br /> Payments_Approvers |                  View items                  |
|                                     Unparsed (details below)                                     |                               Payments_Repairers                                |       View, insert, edit, delete items       |
|                              New SWIFT MT Messages (details below)                               |                                Payments_Creators                                |       View, insert, edit, delete items       |
|                              New SWIFT MX Messages (details below)                               |                                Payments_Creators                                |       View, insert, edit, delete items       |
|                                        Payments_Repairers                                        |                               Payments_Repairers                                |       View, insert, edit, delete items       |
|                                        Payments_Approvers                                        |                               Payments_Approvers                                |       View, insert, edit, delete items       |
| [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Outbox | Payments_Creators<br /><br /> Payments_Repairers<br /><br /> Payments_Approvers |       View, insert, edit, delete items       |

## Unparsed Document Library  
 The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair process deals with messages that fail parsing in a special manner. Unparsed messages (messages that cannot be translated into XML) are routed to a single unparsed message document library. The unparsed document library should be restricted to allow only specific people, rather than entire groups, to access the folder. This will ensure that the unparsed folder is as secure as possible.  

 Users who have permissions to repair unparsed messages need permissions in the repair role for at least one department defined in the MMC configuration console, and also need to be enrolled in the NT Group [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Users Group.  

## New SWIFT MT/ MX Messages Document Library  
 The New SWIFT MT Messages and New SWIFT MX Messages document libraries are created at the time of deploying the MRSR site. The New SWIFT MT Messages and New SWIFT MX Messages document libraries store new SWIFT XML templates or "boilerplate" messages. You can use these messages to create new SWIFT messages represented in InfoPath XML format. These messages are uploaded into the New SWIFT MT Messages and New SWIFT MX Messages document libraries by the user by clicking on the Upload button in the document library. You can further distribute the New SWIFT Message templates to restrict access to specified users. To do so you first create a new document library, and then copy the XML templates required for the document library.  

 For more information about the FormPublish tool, see [FormPublish Tool](http://msdn.microsoft.com/09a6ed31-5917-4776-9a5e-955af440cdac) in the Tools section.