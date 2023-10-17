---
description: "Learn more about: Traditional Single Sign-On Applications"
title: "Traditional Single Sign-On Applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a49bdae7-215a-43fb-875e-f64abb37aef0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Traditional Single Sign-On Applications
The Single Sign-On (SSO) programming architecture contains a mapping component to map between applications and users, a lookup component to look up credentials for a specified use, and an administration component to perform administrative tasks. In addition, SSO also contains a ticketing interface so that your application can issue and redeem tickets.  
  
## Mapping  
 Mapping is the process of linking a specified user with a specified application. You can map between affiliate applications and users who are using `ISSOMapping`, `ISSOMapper`, and `ISSOMapper2`. With `ISSOMapping`, you can create, delete, enable, and disable mappings. With `ISSOMapper`, and `ISSOMapper2`, you can get and set mapping data for the current user.  
  
## Lookup  
 The core of the Single Sign-On programming interface is the ability to look up credentials for specified users. You can look up credentials using `ISSOLookup1`, and `ISSOLookup2`. `ISSOLookup1`, enables the user to retrieve their own external credentials. In contrast, `ISSOLookup2` also enables you to look up the credentials of a remote user for a local affiliate application. The former is necessary for a traditional Single Sign-On application, whereas the latter is useful when you are writing a host-initiated Single Sign-On application.  
  
## Administration  
 You can perform many of the administrative capabilities programmatically through `ISSOAdmin`, `ISSOAdmin2`, and `ISSOConfigStore`. Such tasks include configuring Single Sign-On and creating and describing an application to Single Sign-On. You also can create and modify SSO databases using `ISSOConfigDB`, `ISSOConfigOM`, and `ISSOConfigSS`. Finally, you can administer the password sync features using `ISSOPSAdmin`.  
  
## Communication and Ticketing  
 Your application will most likely issue messages so that your user can communicate with a remote application. To communicate with a remote application more securely, you must issue and redeem a Single Sign-On ticket. You can also issue and redeem tickets programmatically.  
  
## See Also  
 [Single Sign-On Applications](../core/single-sign-on-applications.md)
