---
title: "Configuring A4SWIFT Users | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, user accounts"
  - "creating, user accounts"
  - "user accounts, creating"
ms.assetid: 45dcbece-ec8d-410a-8320-79bfbc4c779d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring A4SWIFT Users
During installation of [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], the A4SWIFT configuration program creates default trading partner profiles and agreements, and registers the BizTalk Server. A4SWIFT also creates document libraries used by the Message Repair and New Submission component.  
  
 A4SWIFT creates the following document folders during installation:  
  
- Outbox document library  
  
- Templates document library  
  
- Unparsed document library  
  
- New SWIFT MT Message document library  
  
- New SWIFT MX Messages document library  
  
  For each department created, the A4SWIFT Administrator must manually set up site groups for the corresponding departments and A4SWIFT defined roles. Each department/role has an inbox created automatically by the Profile Web Client(PWC).  
  
  After the A4SWIFT setup configuration program is completed, the A4SWIFT Administrator configures workflows for each department in the organization. During Message Repair and New Submission configuration, through the Profile Web Client, corresponding inboxes are created for each department/role combination. For example, during PWC configuration an A4SWIFT Administrator creates a department named Payments and then assigns the roles of Creators, Repairers, and Approvers to a department called Payments. Document libraries on the MRSR site are created with the inbox names as shown in the examples in the following table:  
  
|Department name|Role name|Inbox name|  
|---------------------|---------------|----------------|  
|Payments|Creators|Payments_Creator|  
|Payments|Repairers|Payments_Repairers|  
|Payments|Approvers|Payments_Approvers|