---
title: "Administering TN32701 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7b9aec1-472a-480c-bf08-fe74cb0a62d1
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Administering TN3270
Using SNA Manager, you can view client addresses, LU names, and the state of each defined client computer. The session status information is useful if you need to stop, pause, or modify TN3270.  
  
 You can monitor network activity, including the state of each LU. An LU or pool will display one of the following states.  
  
|State|Description|  
|-----------|-----------------|  
|CONNECTED|The TN client has established a connection to TN3270 service.|  
|SSCP-LU|The TN client has established a connection to VTAM.|  
|LU-LU|The LU is bound to a host application.|  
|TERM|The connected session is terminating.|  
  
### To add LUs or pools to TN3270 service  
  
1. Before LUs can be added to the TN3270 service, you must first create application (LUA) LUs on an appropriate connection.  
  
2. 0Select the LUs on the connection.  
  
    A contiguous range of LUs can be selected by using the mouse to select the first item in the range you want to add, holding down the SHIFT key, and using the mouse to select the last item in the range that you want to add.  
  
    A noncontiguous range of LUs can be selected by using the mouse to select each item in the range that you want to add, while holding down the CTRL key.  
  
3. Drag the LUs into the desired server icon in the TN3270 Service folder.  
  
    The LU appears in the list frame when the server icon in the TN3270 Service folder is highlighted. The icon for the LUs will change to a TN icon both in the TN3270 service and in the connection list.  
  
    By default, the LU will be assigned an IP address of 0.0.0.0 and a subnet mask of 0.0.0.0. This will allow any TN3270 client to use this LU.  
  
4. Specify one or more client IP addresses for this LU.  
  
5. On the **Action** menu, click **Save Configuration** to put the changes into effect.  
  
   By adding an LU, you are defining [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] resource access to TN3270 service and you are defining logmode entries that are associated with a Host Integration Server resource.  
  
   Configuration changes are apparent only to users who establish a connection after the configuration changes are saved. Users who were connected at the time that the configuration changes were made will not be affected.  
  
   You can modify, delete, or add IP addresses and subnet masks to LUA LUs. If you want to change the configuration of multiple LUA LUs, you can only change properties such as display types, the IP address, and subnet mask that the LUA LUs have in common. You cannot change properties such as the LUA LU name or number, because these values are unique for each LUA LU.  
  
   You can add new IP addresses and subnet masks to a range of LUA LUs. If the new IP address or subnet mask already exists on some of the LUA LUs, but not on others, the addition will occur without duplication in the ones that already have the IP address or subnet mask. You can also modify or delete the IP addresses that the LUA LUs have in common and that appear on the IP address list.  
  
   You can assign a 3270 LU pool to a workstation, not an LUA pool. LUA pools can be assigned to the TN3270 service.  
  
#### To edit a TN3270 LU configuration  
  
1. In the **SNA Manager** console tree, select the LU that you want to view or modify.  
  
2. Right-click the LU name, and then click **Properties**.  
  
3. Click **OK** to exit.  
  
   TN services listen on multiple ports simultaneously. You can set a default port number for the TN service (assign the port number to the server) and override this number on a per session basis (assign the port number to the LU session), allowing a single client computer to connect to multiple host computers.  
  
#### To override the default port value for a session  
  
1.  Select an LU.  
  
2.  Right click, and then click **Properties**. The **TN3270 LU Properties** dialog box appears.  
  
3.  Click **Use**, and then type a port number other than the default used for the server. The LU port assignment will override the default port assigned to the server.  
  
#### To start, pause, continue, and stop TN3270 service  
  
1. Right-click **TN3270**, and then click **Start** or **Stop**.  
  
    \- or -  
  
2. In the **Services** utility of the Windows **Administrative Tools or Windows Control Panel**, select **TN3270 Service**, and right-click **Start**, **Pause**, **Continue**, or **Stop**.  
  
   The TN3270 service is set to start manually by default. You can change this to automatic if you are not running either the TN5250 service or the Telnet daemon on this server, or if you have configured the TCP ports for more than one of these services.  
  
   Once TN3270 service has stopped, it can no longer be accessed. You may need to start the TN3270 service after you have paused or stopped it. TN3270 service can be restarted only on the local system.  
  
   Pausing allows you to prevent new users from establishing a connection with TN3270 service without disconnecting current users. You can then view TN3270 service session status and notify connected users to disconnect from TN3270 service.  
  
   Before stopping TN3270 service, notify all connected users that they will be disconnected within a specified time period. Stop the service after expiration of your warning period.  
  
### Tips  
  
- To start TN3270 service from a command prompt, type  
  
   **net start tn3270**  
  
- To pause TN3270 service from a command prompt, type  
  
   **net pause tn3270**  
  
- To continue TN3270 service from a command prompt, type  
  
   **net continue tn3270**  
  
- To stop TN3270 service from a command prompt, type  
  
   **net stop tn3270**  
  
  TN3270, TN5250, and Telnet services all default to the well-known TCP port number 23. If you plan to install more than one of these services, perform the following steps.  
  
##### To use TN3270 service with TN5250 service or Telnet service  
  
1.  Configure the services to use unique port numbers.  
  
2.  Reconfigure all your TN3270 clients or TN5250 clients to use the new port numbers.  
  
##### To remove TN3270 service  
  
1. To pause TN3270 service, use the **Services** utility in Windows Control Panel.  
  
2. Pausing TN3270 service allows you to notify connected users to disconnect from TN3270 service before you stop and remove the application.  
  
3. To stop TN3270 service, use the **Services** utility in Windows Control Panel.  
  
4. Open **Control Panel**, and double-click **Add/Remove Programs**.  
  
5. Click **Host Integration Server**, and then click **Change**. The **Add/Remove Application** dialog box appears.  
  
6. In the **Add/Remove** dialog box, click **Add/Remove**.  
  
7. Click the **TM3270 Service** icon, and then click **Entire Feature will be unavailable**.  
  
8. Click **Continue**.  
  
   > [!NOTE]
   >  You can remove TN3270 service anytime you want. However, removing TN3270 service deletes the TN3270 service files from your computer, including TN3270 service configuration data. To use TN3270 service again, you must run [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Setup to reinstall TN3270 service files.  
  
## See Also  
 [TN3270 and Single Sign-On](../core/tn3270-and-single-sign-on1.md)   
 [TN3270](../core/tn32702.md)