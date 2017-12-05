---
title: "Protect the TI Runtime Environment2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 278d9369-5419-4d7f-adbe-9850b6514b01
caps.latest.revision: 3
---
# Protect the TI Runtime Environment
To prevent an attacker from instantiating multiple Transaction Integrator (TI) components to launch a denial of service attack on the TI runtime environment, you should:  
  
-   Store all TI component type libraries and .NET assemblies in a secure directory.  
  
-   Confirm that the access permissions on all type libraries and .NET assemblies are set correctly.  
  
-   Confirm that the access permissions on the directory where the type libraries and .NET assemblies are stored are set correctly.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation1.md)