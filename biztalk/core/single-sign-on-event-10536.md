---
title: "Single Sign-On: Event 10536 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d493a45b-c4ed-40fc-8803-b3ca12f9795b
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10536
## Details  

|                 |                                                                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                     Enterprise Single Sign-On                                                                                      |
| Product Version |                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                     |
|    Event ID     |                                                                                               10536                                                                                                |
|  Event Source   |                                                                                               ENTSSO                                                                                               |
|    Component    |                                                                                                 CO                                                                                                 |
|  Symbolic Name  |                                                                                         SSO_WARN_API_AUDIT                                                                                         |
|  Message Text   | SSO AUDIT%r<br /><br /> Function: %1%r<br /><br /> Tracking ID: %2%r<br /><br /> Client Computer: %3%r<br /><br /> Client User: %4%r<br /><br /> Application Name: %5%r<br /><br /> Error Code: %6 |

## Explanation  
 This Warning Audit event indicates that an event that meets the user defined audit level has occurred. This event message includes:  

 **Function:** Function being performed  

 **Tracking ID:** Unique GUID generated when an SSO API is first called.  

 **Client Computer:** Client computer where the function originated.  

 **Client User:** The name of the user account that invoked the function.  

 **Application Name:** Name of the SSO affiliate application associated with this function.  

 **Error Code:** Unique error identifier.  

 This type of event is used for diagnosing problems during development, troubleshooting, or running of an application. Information provided can be used to determine the SSO API call being made.  

 The audit level can be set to 0/1/2/3 – 0 means “none”, 1 means “low” displays errors only, 2 means “medium” displays errors and warnings, and 3 means “high” displays all audit messages.  

## User Action  

- Check the event log for associated event messages.  

  For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:  

- [How to Audit SSO](../core/how-to-audit-sso.md)  

- [Using SSO](../core/using-sso.md)
