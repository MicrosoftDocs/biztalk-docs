---
title: "Protect the Local File System, Database, and Registry1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b101b7c6-5daa-4019-8782-797a6d7ebeaf
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Protect the Local File System, Database, and Registry
To prevent an attacker from spoofing their identity, accessing restricted data, or tampering with the data, you should do the following:  
  
- Place the computer that is running Transaction Integrator (TI) in a secure location.  
  
- Confirm that the access permissions to TI programs, TI components, and the registry are set correctly.  
  
- Use host-initiated Single Sign-On (SSO) in conjunction with valid host UID and PWD passed in the initial connection flows.  
  
- Use a secure network connection (for example, CICS TRM over IPsec-protected TCP/IP network connection).  
  
  You can also help mitigate this threat with the following deployment scenarios:  
  
- Host-initiated SSO  
  
  You can learn more about this threat by reading about the following:  
  
- How to help secure remote access to SQL Server (for example, integrated Windows security)  
  
- How to send a valid host user ID  
  
- How to send a valid host password  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)   
 [Single Sign-On in Transaction Integrator](../core/single-sign-on-in-transaction-integrator2.md)   