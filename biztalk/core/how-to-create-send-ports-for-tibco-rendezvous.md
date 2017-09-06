---
title: "How to Create Send Ports for TIBCO Rendezvous | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating send ports"
  - "ports, send"
  - "send ports, creating"
ms.assetid: 0c8d9fdc-b273-4876-9f93-b5a85539a3c1
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Send Ports for TIBCO Rendezvous
Follow these steps to create a send port using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
### To create a send port  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
2.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
3.  In the **Send Port Properties** dialog box, do the following:  
  
    1.  Type a name for the send port, for example, `SendToTIBCORV`.  
  
    2.  From the **Type** drop-down list, select **TIBCO Rendezvous**.  
  
    3.  From the **Send handler** drop-down list, select the URI.  
  
    4.  From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
    6.  Click **Configure** to configure the send port.  
  
4.  In the **TIBCO Rendezvous Transport Properties** dialog box, do the following:  
  
    1.  Enter the properties.  
  
         You do not have to set the logon information.  
  
    2.  In the list, select the SSO affiliate application you created to represent the TIBCO Rendezvous system.  
  
    3.  For **Use SSO**, select **Yes**.  
  
    4.  Click **OK**.  
  
5.  Click **OK**.  
  
## See Also  
 [Creating TIBCO Rendezvous Send Handlers](../core/creating-tibco-rendezvous-send-handlers.md)