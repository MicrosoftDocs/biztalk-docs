---
title: "TN3270 Access1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6254db28-9650-4c2e-8174-ec591b49bc14
caps.latest.revision: 6
---
# TN3270 Access
TN3270 is a type of Telnet service that allows access to mainframe computers over a TCP/IP network. Users can connect to mainframes using a TN3270 client and the TN3270 service provided with Host Integration Server.  
  
 The TN3270 service supports these protocols:  
  
-   TN3270, for display sessions  
  
-   TN3287, for printer sessions  
  
-   TN3270E, for extended display and print sessions  
  
 The TN3270 service uses Host Integration Server features to provide mainframe access and to address issues such as security and redundancy when the data communications path between the client and server contains one or more nonsecured segments.  
  
## TN3270 Service  
 The TN3270 service communicates with Host Integration Server using the LUA (Logical Unit for Applications) API. Because of this, LUA-type connections and LUs must be configured on the server. Once configured, LUA LUs and LU pools can be assigned to the TN3270 service and made available for use by TN3270 clients requesting mainframe access.  
  
## In This Section  
 [Deployment Strategies (TN3270)](../HIS2010/deployment-strategies-tn3270-1.md)  
  
## See Also  
 [Setting Port Numbers (TN3270)](../HIS2010/setting-port-numbers-tn3270-2.md)   
 [Deploying Hot Backup and Load Balancing (TN3270)](../HIS2010/deploying-hot-backup-and-load-balancing-tn3270-2.md)   
 [Assigning LUs to an IP Address (TN3270)](../HIS2010/assigning-lus-to-an-ip-address-tn3270-2.md)   
 [Planning 3270 Connectivity](../HIS2010/planning-3270-connectivity1.md)