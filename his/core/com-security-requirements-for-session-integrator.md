---
title: "COM Security Requirements for Session Integrator1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff94595f-c07d-4da4-b05c-d5c8801d075d
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# COM Security Requirements for Session Integrator
When using Session Integrator in an environment where the Client application and the Service component are running under two different user accounts, special configuration of COM security should be performed.  
  
#### To configure COM security in Component Services  
  
1.  Click Start, then click Run, then type `DCOMCNFG`, and then click **OK**.  
  
2.  In Component Services, expand **Component Services**, expand **Computers**, right-click My **Computer**, and then click **Properties**.  
  
3.  In **My Computer Properties**, in the **COM Security** tab, under **Access Permissions**, click **Edit Default**.  
  
4.  In **Access Permission** dialog box, click **Add** to add the Server user context. If the Server is not on the same computer as the client, you must allow Remote Access to the user.  
  
5.  Click **OK** twice.