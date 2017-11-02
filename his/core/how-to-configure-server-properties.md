---
title: "How to Configure Server Properties2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20320207-d9f0-4f21-9c8f-0c4482b9e64a
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Configure Server Properties
The **Server Configuration** dialog box can be used to change [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] properties, including:  
  
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
 [IP-DLC Link Service](../Topic/IP-DLC%20Link%20Service1.md)   
 [SNA Manager](../core/sna-manager.md)   
 [How to Open a Subdomain](../core/how-to-open-a-subdomain.md)   
 [How to Configure SNA Service Properties](../core/how-to-configure-sna-service-properties.md)   
 [Important Configuration Information](../core/important-configuration-information.md)