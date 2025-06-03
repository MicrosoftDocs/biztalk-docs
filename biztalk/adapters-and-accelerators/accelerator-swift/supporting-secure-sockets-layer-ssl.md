---
description: "Learn more about: Supporting Secure Sockets Layer (SSL)"
title: "Supporting Secure Sockets Layer (SSL)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Supporting Secure Sockets Layer (SSL)
To implement the Secure Sockets Layer (SSL) protocol in your deployment between the client computers and the MRSR servers, you need to request and configure a "Server Authentication" certificate on your Internet Information Services (IIS) servers.  
  
 One certificate should be used for all the servers in your Network Load Balancing (NLB) cluster. You should ensure that the name used in the certificate request is the virtual host name instead of an individual server name.
