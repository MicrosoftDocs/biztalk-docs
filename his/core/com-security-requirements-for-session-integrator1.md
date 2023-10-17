---
description: "Learn more about: COM Security Requirements for Session Integrator"
title: "COM Security Requirements for Session Integrator1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# COM Security Requirements for Session Integrator
When using Session Integrator in an environment where the Client application and the Service component are running under two different user accounts, special configuration of COM security should be performed.  
  
#### To configure COM security in Component Services  
  
1.  Click Start, then click Run, then type `DCOMCNFG`, and then click **OK**.  
  
2.  In Component Services, expand **Component Services**, expand **Computers**, right-click My **Computer**, and then click **Properties**.  
  
3.  In **My Computer Properties**, in the **COM Security** tab, under **Access Permissions**, click **Edit Default**.  
  
4.  In **Access Permission** dialog box, click **Add** to add the Server user context. If the Server is not on the same computer as the client, you must allow Remote Access to the user.  
  
5.  Click **OK** twice.
