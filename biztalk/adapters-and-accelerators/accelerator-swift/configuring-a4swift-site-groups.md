---
title: "Configuring A4SWIFT Site Groups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "site groups, creating"
  - "creating, site groups"
  - "security, user accounts"
  - "user accounts, site groups"
  - "site groups, user accounts"
ms.assetid: ec2f3efe-439a-4018-ad94-5ab0fb2808ee
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring A4SWIFT Site Groups
You need to create the corresponding site groups to lock down the permissions on the document libraries created during Message Repair and New Submission configuration. To do so with the example in the preceding section, an A4SWIFT Administrator would go to the MRSR site and set up the following site groups:  
  
- Payments_Creators  
  
- Payments_Repairers  
  
- Payments_Approvers  
  
  For each of these site groups the following permissions should be applied:  
  
- **View Items.** View items in lists, documents in document libraries, view Web discussion comments, and set up e-mail alerts for lists.  
  
- **View Pages.** View pages in a Web site.  
  
  For each user who participates in the roles for the Payments department, you need to create a new site user and assign that user to the site group that corresponds to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] roles created during MMC configuration.