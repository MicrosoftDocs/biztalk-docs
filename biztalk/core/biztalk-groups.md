---
title: "BizTalk Groups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Management database, groups"
  - "groups"
  - "groups, Management database"
  - "groups, about groups"
ms.assetid: 197cbcf6-c722-4cbb-9642-3cb8a34757e2
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Groups

## Overview
The *BizTalk group* is a unit of organization that usually represents an enterprise, department, hub, or other business unit that requires a contained BizTalk Server implementation. The BizTalk group has a one-to-one relationship with a BizTalk Server Management database (known as the BizTalk Server Configuration database in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).  
  
> [!NOTE]
>  While [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groups may contain multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers, any given [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer may only be associated with a single [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.  
  
 The BizTalk Management database stores configuration information for the BizTalk group and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in that group. This configuration information specifies part of the message-processing logic for the servers and where this logic will physically run. For more information about the BizTalk Server Management database, see [Databases in BizTalk Server](../core/databases-in-biztalk-server.md).  
  
 You must specify the same BizTalk Server Management database for each server installation in the group so that you can administer each server from the administration console.  
  
## See Also  
 [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   
 [Managing Groups](../core/managing-groups.md)   
 [Entities](../core/entities.md)