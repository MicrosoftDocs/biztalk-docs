---
title: "Supporting Secure Sockets Layer (SSL) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSL"
ms.assetid: 012a5be0-bab8-4a60-9d63-b9684b91e4a7
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Supporting Secure Sockets Layer (SSL)
To implement the Secure Sockets Layer (SSL) protocol in your deployment between the client computers and the MRSR servers, you need to request and configure a "Server Authentication" certificate on your Internet Information Services (IIS) servers.  
  
 One certificate should be used for all the servers in your Network Load Balancing (NLB) cluster. You should ensure that the name used in the certificate request is the virtual host name instead of an individual server name.