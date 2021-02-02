---
description: "Learn more about: Choosing IP Settings"
title: "Choosing IP Settings1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b36d5710-5322-4050-8ee0-78511ef8dca2
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Choosing IP Settings
IP settings assigned to the TN5250 definitions allow TN5250 clients to connect to the AS/400. By default, the TN5250 definition is not assigned an IP address or a subnet mask. This allows any TN5250 client to connect to the AS/400.  
  
 You can restrict access to the TN5250 service by specifying the IP address or subnet mask of the client workstation(s). When these values are specified, only clients whose IP and/or subnet mask match those specified in the TN5250 configuration are allowed access to the AS/400 through the TN5250 service. You can also specify the workstation name in place of the IP, and use a WINS, DHCP, or other name-resolution service to resolve a friendly name to an IP address.
