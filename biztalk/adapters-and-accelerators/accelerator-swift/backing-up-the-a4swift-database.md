---
title: "Backing Up the A4SWIFT Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up A4SWIFT database"
  - "A4SWIFT database, backing up"
ms.assetid: 53e46380-5be7-4d4c-b04c-d917ab40c07c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Backing Up the A4SWIFT Database
You should routinely back up the databases in your BizTalk Server and A4SWIFT system to lower the risks of a catastrophic failure. These databases include those in your BizTalk Server source system, and the A4SWIFT database. In addition to lowering risks, this will also enable you to purge A4SWIFT history files that can grow to a significant size.  
  
 For more information about backing up the databases in your BizTalk Server source system, see the "Backing Up and Restoring BizTalk Server Databases" topic in the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help. This topic describes the Backup BizTalk Server job that you use to back up BizTalk databases.  
  
 For information about backing up the A4SWIFT database, see the "How to Back Up Custom Databases" topic in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help. This topic describes how to modify the Backup BizTalk Server job to include the custom A4SWIFT database.