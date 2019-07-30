---
title: "Protect the TI Runtime Environment1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: de0c7dba-9754-485e-b989-5cd385e81a27
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Protect the TI Runtime Environment
To prevent an attacker from instantiating multiple Transaction Integrator (TI) components to launch a denial of service attack on the TI runtime environment, you should:  
  
-   Store all TI component type libraries and .NET assemblies in a secure directory.  
  
-   Confirm that the access permissions on all type libraries and .NET assemblies are set correctly.  
  
-   Confirm that the access permissions on the directory where the type libraries and .NET assemblies are stored are set correctly.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)