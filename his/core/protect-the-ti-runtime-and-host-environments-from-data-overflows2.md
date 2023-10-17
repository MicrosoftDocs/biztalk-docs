---
description: "Learn more about: Protect the TI Runtime and Host Environments from Data Overflows"
title: "Protect the TI Runtime and Host Environments from Data Overflows2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Protect the TI Runtime and Host Environments from Data Overflows
To prevent an attacker from using inbound, unbounded recordsets to launch a denial of service attack on either the Transaction Integrator (TI) runtime or host environment, you should:  
  
-   Store all TI component type libraries and .NET assemblies in a secure directory.  
  
-   Confirm that the access permissions on all type libraries and .NET assemblies are set correctly.  
  
-   Confirm that the access permissions on the directory where the type libraries and .NET assemblies are stored are set correctly.  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation2.md)
