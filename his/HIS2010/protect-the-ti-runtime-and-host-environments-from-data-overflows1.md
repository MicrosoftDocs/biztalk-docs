---
title: "Protect the TI Runtime and Host Environments from Data Overflows1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9845cda1-9e15-4d23-86e9-97557468aa89
caps.latest.revision: 4
---
# Protect the TI Runtime and Host Environments from Data Overflows
To prevent an attacker from using inbound, unbounded recordsets to launch a denial of service attack on either the Transaction Integrator (TI) runtime or host environment, you should:  
  
-   Store all TI component type libraries and .NET assemblies in a secure directory.  
  
-   Confirm that the access permissions on all type libraries and .NET assemblies are set correctly.  
  
-   Confirm that the access permissions on the directory where the type libraries and .NET assemblies are stored are set correctly.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../HIS2010/transaction-integrator-threat-mitigation1.md)