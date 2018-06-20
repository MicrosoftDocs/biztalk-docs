---
title: "Single Sign-On: Event 10749 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10986736-77c0-42a7-b2bb-cd20f9f75fa6
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10749
## Details  

|                 |                                                                                                                                                                                                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                      Enterprise Single Sign-On                                                                                                                      |
| Product Version |                                                                                                     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                      |
|    Event ID     |                                                                                                                                10749                                                                                                                                |
|  Event Source   |                                                                                                                               ENTSSO                                                                                                                                |
|    Component    |                                                                                                                                 N\A                                                                                                                                 |
|  Symbolic Name  |                                                                                                                       SSO_WARN_PS_CLIENT_PING                                                                                                                       |
|  Message Text   | Could not contact the destination SSO server.<br /><br /> Check that the SSO service is running on that server and that it can be contacted.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> SSO Server Name: %3%r<br /><br /> Error Code: %4 |

## Explanation  
 This Warning event indicates that SSO Password Sync could not contact the specified destination SSO server.  

## User Action  
 To resolve this warning, do one or more of the following:  

- Use the ENTSSO Servers Snap-In to check the server.  

- Start the Enterprise Single Sign-On Service if it is not running.  

- Check the network connection to the destination SSO server.  

- Check firewall on the destination SSO Server.  

  For more information, see the following resources:  

- [How to Use the Servers Snap-in](../core/how-to-use-the-servers-snap-in.md)
