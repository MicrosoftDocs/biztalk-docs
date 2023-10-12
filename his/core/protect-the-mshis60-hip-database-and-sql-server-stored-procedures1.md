---
description: "Learn more about: Protect the MSHIS60_HIP Database and SQL Server Stored Procedures"
title: "Protect the MSHIS60_HIP Database and SQL Server Stored Procedures1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Protect the MSHIS60_HIP Database and SQL Server Stored Procedures
To prevent an attacker from spoofing their identity or tampering with the data or stored procedures in the HIP database, you should do the following:  
  
- Run the HIP Service in a valid Windows privileged account and use Windows integrated security to access the HIP SQL Server database.  
  
- Allow only privileged accounts access to the HIP SQL Server database.  
  
- Use a local SQL Server database and do not allow remote access.  
  
- Use only Windows integrated security and restrict access to only privileged Windows accounts.  
  
  You can also help mitigate this threat with the following deployment scenarios:  
  
- Service-based Security  
  
- Host-initiated Single Sign-On (SSO).  
  
  You can learn more about this threat by reading about:  
  
- How to secure remote access to SQL Server (for example, integrated Windows security).  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)
