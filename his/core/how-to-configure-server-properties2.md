---
title: "How to Configure Server Properties2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20320207-d9f0-4f21-9c8f-0c4482b9e64a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Server Properties
The **Server Configuration** dialog box can be used to change [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] properties, including:  
  
-   Server Name  
  
-   Subdomain Name  
  
-   Active Directory OU Name  
  
-   Server Role - Primary or Backup  
  
-   Restart - MngAgent and SnaBase  
  
### To configure server properties  
  
1.  Start SNA Manager.  
  
2.  In SNA Manager, right-click the server, and select **Properties**.  
  
3.  To change the server name, click **Change** near the top of the **Server Configuration** tab. Note that the server must be offline before you can change the name.  
  
4.  To set the Group Identity (Subdomain name and Active Directory), Server Role (Primary or Backup), or Network Transports (TCP/IP is default), click **Change** near the bottom of the **Server Configuration** tab.  
  
5.  Make the appropriate changes to your configuration, and then click **OK**.  
  
6.  You must save your configuration to keep the properties you set. Right-click the server, and click **Save Configuration**.  
  
## See Also  
 [IP-DLC Link Service](./ip-dlc-link-service2.md)   
 [SNA Manager](../core/sna-manager1.md)   
 [How to Open a Subdomain](../core/how-to-open-a-subdomain1.md)   
 [How to Configure SNA Service Properties](../core/how-to-configure-sna-service-properties1.md)   
 [Important Configuration Information](../core/important-configuration-information2.md)