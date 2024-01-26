---
description: "Learn more about: Server Configuration"
title: "Server Configuration1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_Server_Change"
---
# Server Configuration
**Subdomain Name**  
 Displays the SNA subdomain that this server is a member of. To change the subdomain name, enter a new subdomain name and click **Save**.  
  
 **Active Directory Client Support**  
 If selected, this server is part of the Active Directory Organizational Unit (OU) as shown in the **Active Directory OU Name:** field. To change the OU, enter a new OU name and click **Save**.  
  
 **Role**  
 Select how this server will be configured, either as a **Primary Configuration Server** or a **Backup Configuration Server**.  
  
 **Network Transports**  
 Select all network transport protocols that this server will use on the network.  
  
 **Services**  
 The **Services** box shows the status of the **MngAgent** and **SnaBase** services. If these services are running, you must restart them before changes to the subdomain, server role, or network transports will take effect.  
  
 **Restart**  
 Click **Restart** to restart services required for changes to the subdomain, server role, or network transports to take effect. **Restart** is active only if you change the configuration of another server. If you want to change the configuration of the server on which you are currently working, **Restart** is unavailable. For changes to take effect on your server, close SNA Manager, open **Control Panel**, open **Services**, and then **Stop** and **StartSNA MngAgent** and **SnaBase**.  
  
 **Save**  
 Click **Save** to save your server configuration changes.  
  
> [!IMPORTANT]
>  Changing server configuration parameters can have serious consequences. Restarting the server will cause all connections and sessions to be disconnected. Notify all users prior to restarting.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)
