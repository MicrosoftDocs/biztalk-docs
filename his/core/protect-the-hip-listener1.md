---
title: "Protect the HIP Listener1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 90eb8a82-48db-42f5-a5ce-f1f38f91abc1
caps.latest.revision: 4
---
# Protect the HIP Listener
To prevent an attacker from spoofing their identity, tampering with the data, or denying service, you should run the HIP services in valid Windows privileged account.  
  
### To protect the HIP listener  
  
1.  Click **Start**, click **Control Panel**, double-click **Administrative Tools**, and then double-click **Services**.  
  
2.  In the details pane, right-click **HIPService**, and then click **Properties**.  
  
3.  Click **This account**,and then specify a valid Windows privileged account.  
  
4.  Type the password for the user account in **Password** and in **Confirm password**, and then click **OK**. If you select the **Network Service** account, the password must be blank.  
  
 You can also help mitigate this threat with the following deployment scenario:  
  
-   Service-based security  
  
## See Also  
 [Transaction Integrator Threat Mitigation](../core/transaction-integrator-threat-mitigation1.md)   
 [Services Account Screen](../core/services-account-screen2.md)