---
title: "Securing Host Integration Server Files and Directories2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37f261e2-c09d-414e-9ce1-2da5233eff6e
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Securing Host Integration Server Files and Directories
If you install Host Integration Server onto an NTFS volume, you can control which SNA subdomain users can modify the Host Integration Server configuration file. A Host Integration Server administrator can control access to the configuration using the Host Integration Server SNA Manager. By specifying access permissions for users, you can control who has the ability to administer, change, or view a configuration.  
  
 When you install Host Integration Server, you create a single directory tree that contains the files needed to configure and use Host Integration Server. To control access to the configuration files in these shares, use the following guidelines:  
  
- Create domain user accounts to run the SnaBase and SnaServer services. A domain user account is one that is allowed to log on to the network.  
  
- Disable the Windows domain guest account.  
  
  At least one domain user or group must have Full Control permissions over all the shares, preferably a trusted group such as Administrators. If no user or group has Full Control permissions, the only person who can change the share permissions is the owner of the share. If necessary, this individual can change his or her permissions to Full Control as needed.  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security1.md)