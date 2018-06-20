---
title: "Protect the .NET Servers1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe8600ff-a1ff-4b81-aa3d-b002959a98fb
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Protect the .NET Servers
To prevent an attacker from spoofing their identity, tampering with the data on the host, elevating their privileges, accessing restricted data, or denying service, you should:  
  
- Use static IP addresses on the host  
  
- Run server components in-process with a HIP Service account.  
  
  You can also help mitigate this threat with the following deployment scenario:  
  
- Send properly-formatted messages (for example, ELM, TRM, DPL, SNA, IP)  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)