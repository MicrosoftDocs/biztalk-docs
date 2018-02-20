---
title: "Determining Who Initiated a Transaction2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3458fda8-e663-46e8-8e96-5a0e32ecca69
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Determining Who Initiated a Transaction
You can easily determine who initiated a specific transaction. This is helpful, for example, when you need to track down the history of a transaction failure. You can also use this technique to implement resource or transaction-level, per user, security.  
  
 When you select either user-level or package-level security on the **Security** tab of the Transaction Integrator (TI) Remote Environment (RE) properties page, TI sends security information in the session request to the host. You can deploy the Host Account Mapping database known as the Host Account Cache (HAC), and set up a mapping between each Windows user and the corresponding host user ID, and that is what TI will send. Or you can use the **Allow application to override security** option on the **Security** tab, and have the application return any host user ID (and password).  
  
 Whether the host will do anything with the different user IDs depends mostly on the ATTACHSEC setting for the CICS connection; this corresponds to the APPC LU that TI uses. The default ATTACHSEC setting is **local**, meaning that CICS does not validate the user ID in the session, and CICS runs the transaction in a default host credential. But if you set the ATTACHSEC setting, CICS uses Resource Access Control Facility (RACF) to validate the user ID in the session, and CICS then attaches that user ID to the trusted computing base (TCB) for the transaction as it runs through the Mirror transaction into the target mainframe transaction program.  
  
## See Also  
 [Meeting Specific Real-World Needs](../core/meeting-specific-real-world-needs2.md)