---
title: "Deployment Overview1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6baae608-dd20-4087-aad0-60e2c79e90ab
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Deployment Overview
The system in this example is deployed over three domains, and contains the following computers:  
  
 **Domain ORCH.com**  
  
- ORCH domain controller  
  
- HIS1, the HISSO server  
  
- HIS2, the master secret server  
  
- HIS3, the Admin database  
  
  **Domain SQL.com**  
  
- SQL domain controller  
  
- SQL2, the SSO database  
  
  **Domain HIS.com**  
  
- HIS domain controller  
  
- HIS4 database  
  
  The key points defining this deployment are as follows:  
  
- Domain ORCH.com and domain SQL.com have a two-way selective trust relationship.  
  
- Domain ORCH.com is configured as native Windows Server functional level.  
  
- All SSO services are running on an ORCH.com domain user account (Orch\SSOSvcUser). The user is configured to have access permission on the SQL2 machine in the SQL.com domain. The user is configured for protocol transition and constrain delegation within the ORCH.com domain.  
  
- Another ORCH.com domain user (Orch\TestAppUser) is set for running test programs. This user is also configured for protocol transition and constrain delegation.  
  
  For a description of the deployment process, see [Deployment Process](../esso/deployment-process.md)  
  
## See Also  
 [Secure Deployment of Enterprise Single Sign-On](../esso/secure-deployment-of-enterprise-single-sign-on.md)   
 [Deployment Process](../esso/deployment-process.md)