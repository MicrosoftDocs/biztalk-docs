---
title: "SSO Deployment Overview | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSO, deploying example"
  - "SSO, deploying"
  - "deploying, SSO"
  - "SSO, multiple computers"
  - "examples, deploying"
ms.assetid: 6eccee26-c392-41fe-97fb-3afe1685540f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO Deployment Overview
The system in this example is deployed over three domains, containing the following computers:  
  
 **Domain ORCH.com**  
  
- ORCH domain controller  
  
- HIS1, the HISSO server  
  
- HIS2, the Master Secret Server  
  
- HIS3, the Admin database  
  
  **Domain SQL.com**  
  
- SQL domain controller  
  
- SQL2, the SSO database  
  
  **Domain HIS.com**  
  
- HIS domain controller  
  
- HIS4 database  
  
  The key points defining this deployment are as follows:  
  
- Domain ORCH.com and domain SQL.com have a two-way selective trust relationship.  
  
- Domain ORCH.com is configured as native [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] functional level.  
  
- All SSO services are running on an ORCH.com domain user account (Orch\SSOSvcUser). The user is configured to have access permission on the SQL2 machine in the SQL.com domain. The user is configured for protocol transition and constrain delegation within the ORCH.com domain.  
  
- Another ORCH.com domain user (Orch\TestAppUser) is set for running test programs. This user is also configured for protocol transition and constrain delegation.  
  
## See Also  
 [Deployment Process](../core/deployment-process.md)