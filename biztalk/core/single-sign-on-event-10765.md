---
description: "Learn more about: Single Sign-On: Event 10765"
title: "Single Sign-On: Event 10765"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10765
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10765                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N/A                             |
|  Symbolic Name  |                  ENTSSO_E_NO_CREDENTIALS                   |
|  Message Text   |       No credentials have been set for the mapping.        |
  
## Explanation  
 You have requested a GetCredentials on a mapping, and the mapping specified has no credentials.  
  
## User Action  
 Use the command line or the MMC Snap-in to set credentials for the mapping.
