---
title: "How to Create Send Ports for TIBCO Enterprise Message Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating send ports"
  - "ports, send"
  - "send ports, creating"
ms.assetid: 6e569244-494e-4db4-8030-eda3b390d073
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Send Ports for TIBCO Enterprise Message Service
Follow these steps to create a send port.  
  
## Creating a Send Port  
  
#### To create a send port  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
2.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
3.  In the **Send Port Properties** dialog box, do the following:  
  
    1.  Type a name for the send port, for example, `SendToTIBCOEMS`.  
  
    2.  From the **Type** drop-down list, select **TIBCO EMS**.  
  
    3.  From the **Send handler** drop-down list, select the URI.  
  
    4.  From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
    6.  Click **Configure** to configure the send port.  
  
4.  In the **TIBCO EMS Transport Properties** dialog box, do the following:  
  
    1.  Enter **Message Handling**, **Server Connection Definition**, **Transaction Support**, **Username**, and the **password**.  
  
         You do not have to set the logon information.  
  
    2.  In the list, select the affiliate application you created to represent the TIBCO EMS system.  
  
    3.  For **Use SSO**, select **Yes**.  
  
    4.  Click **OK**.  
  
5.  Click **OK**.  
  
## See Also  
 [Setting TIBCO Enterprise Message Service Transport Properties for the Send Port](../core/setting-tibco-enterprise-message-service-transport-properties-for-the-send-port.md)   
 [Creating  TIBCO Enterprise Message Service Send Handlers](../core/creating-tibco-enterprise-message-service-send-handlers.md)