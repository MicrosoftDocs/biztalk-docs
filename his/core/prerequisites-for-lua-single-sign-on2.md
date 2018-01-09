---
title: "Prerequisites for LUA Single Sign-On2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 006dd897-e614-4649-8bdb-610c1db38381
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Prerequisites for LUA Single Sign-On
In preparation for using Single Sign-On over 3270 logical unit for application (LUA LUs), the system administrator must define an Enterprise Single Sign-On Affiliate Application. This host security domain must be initially created or modified to enable the Single Sign-On feature. The system administrator must enable a user’s Windows account in the ESSO database and either the administrator or the user must establish a mapped host account for the Windows domain user name.  
  
 The user must be logged on to a Windows domain with a user name and password. Note that this Single Sign-On feature is only supported over LUA LUs.