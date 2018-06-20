---
title: "Single Sign-On: Event 11061 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52fb18e2-4482-4cdb-b8ed-d579a95acd7c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 11061
## Details  
  
|                 |                                                                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                     Enterprise Single Sign-On                                                                                                                     |
| Product Version |                                                                                                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                     |
|    Event ID     |                                                                                                                               11061                                                                                                                               |
|  Event Source   |                                                                                                                              ENTSSO                                                                                                                               |
|    Component    |                                                                                                                                N/A                                                                                                                                |
|  Symbolic Name  |                                                                                                                   SSO_WARN_BAD_PASSWORD_FILTER                                                                                                                    |
|  Message Text   | The password filter string is not valid. No password filter will be used.%r<br /><br /> Application Name: %1%r<br /><br /> Password Filter String: %2%r<br /><br /> Number Of Tokens Processed: %3%r<br /><br /> Additional Data: %4%r<br /><br /> Error Code: %5 |
  
## Explanation  
 An invalid password filter has been created manually. At some point in this process an error was introduced (see Password Filter String in the warning text for the location of the error).  
  
## User Action  
 To create the Password Filter using the Create Password Filter Wizard, see [How to Use Password Filters](../core/how-to-use-password-filters.md).