---
title: "Remotely Administering Transaction Integrator1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a34042b2-8c04-48d6-a783-485687477e27
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Remotely Administering Transaction Integrator
Transaction Integrator (TI) does not support remote installation or configuration, and it does not support remote administration of Windows-initiated processing (WIP) except through use of the Windows Remote Desktop. TI does support remote administration of host-initiated processing through the use of TI Manager and the Remote Desktop. TI also supports the use of remote SQL Server databases.  
  
## Remote Installation and Configuration  
 TI must be installed and configured locally, and it does not support remote installation or configuration. The only way to install TI Manager and the TI runtime is by using the **Host Integration Server Installation Wizard**, and selecting **Application Integration** on the options page. You cannot install TI Manager or the TI runtime programmatically.  
  
## Remote Administration of Windows-Initiated Processing  
 You can administer Windows-initiated processing only from the local computer, and TI does not support remote administration for WIP. Each computer that has TI installed and configured and that is used for WIP is administratively separate from any other computer that also has TI installed. If you need to administer WIP when you are away from the local computer, you must use the Windows Remote Desktop feature to access TI Manager and the TI runtime.  
  
## Remote Administration of Host-Initiated Processing  
 You can administer the host-initiated processing remotely, but only from a computer that also has TI installed on it and uses the same HIP configuration database. For example, if three servers each have TI installed on them, and all three are configured to use the same HIP database, then you can remotely administer any of the three servers from either of the other two servers. You cannot remotely administer the TI runtime from another server that has TI installed but uses a different HIP configuration database. For example, if you have a fourth server that also has TI installed but uses a different HIP configuration database from the three servers in the previous example, you cannot remotely administer the TI runtime on any of the three other servers. Neither can you remotely administer the fourth server from any of the other three servers.  
  
 If you need to administer HIP when you are away from a computer that is configured to use the same HIP configuration database, you must use the Windows Remote Desktop feature to access TI Manager and the TI runtime.  
  
## Use of Remote Databases  
 You can also configure TI to use a remote SQL Server database. The SQL Server database is used to store TI host-initiated processing (HIP) configuration data. Use the **Microsoft Host Integration Server Configuration Wizard** to specify the database server to use.  
  
#### To configure a remote database  
  
1. Click **Start**, point to **Programs**, point to **Microsoft Host Integration Server**, and then click **Configuration Wizard**.  
  
2. Follow the directions on the screen.  
  
3. On the **Database configurations** wizard page, select **Transaction Integrator Configuration Database**.  
  
4. Click **Edit**.  
  
5. In the **Transaction Integrator Configuration Database Properties** dialog box, select the remote server and database to be used.  
  
6. Click **OK**, and then click **Next**.  
  
7. Continue to follow the directions on the screen.  
  
   After you click **Finish** in the Wizard, TI installs the HIP database on the designated remote server.  
  
## See Also  
 [Getting Started with TI](../core/getting-started-with-ti1.md)   
 [Windows-Initiated Processing Overview](../core/windows-initiated-processing-overview2.md)   
 [Working with Host-Initiated Processing](../core/working-with-host-initiated-processing1.md)