---
title: "Protect the TI Runtime and Host Environments from Data Overflows2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13fa9b00-c95f-457f-84d4-7eb86c7741c1
caps.latest.revision: 4
---
# Protect the TI Runtime and Host Environments from Data Overflows
To prevent an attacker from using inbound, unbounded recordsets to launch a denial of service attack on either the Transaction Integrator (TI) runtime or host environment, you should:  
  
-   Store all TI component type libraries and .NET assemblies in a secure directory.  
  
-   Confirm that the access permissions on all type libraries and .NET assemblies are set correctly.  
  
-   Confirm that the access permissions on the directory where the type libraries and .NET assemblies are stored are set correctly.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation.md)