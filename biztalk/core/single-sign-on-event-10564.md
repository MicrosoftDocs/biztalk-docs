---
description: "Learn more about: Single Sign-On: Event 10564"
title: "Single Sign-On: Event 10564"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 10564
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------|
|  Product Name   |                 Enterprise Single Sign-On                  |
| Product Version | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    Event ID     |                           10564                            |
|  Event Source   |                           ENTSSO                           |
|    Component    |                            N/A                             |
|  Symbolic Name  |           SSO_ERROR_BACKUP_FILE_INCORRECT_FORMAT           |
|  Message Text   |     The backup file does not have the correct format.      |
  
## Explanation  
 The backup file does not have the correct format.  
  
## User Action  
 Check that you have the correct file and location. You should also confirm that there are no other files in that folder with the .BAK extension, as the ENTSSO system may confuse them with the actual backup file.
