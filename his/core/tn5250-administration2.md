---
title: "TN5250 Administration2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05cba61b-4a44-4ef1-a9b7-d8d45ea369a5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TN5250 Administration
The local LU, remote LU, and mode must match the configuration information in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
 To enable an APPC session with the AS/400, the user ID and password must be provided for conversation security. Contact your AS/400 administrator for the correct information.  
  
 The TN5250 requires TN5250/AS400 definition terminal names to allow TN5250 service to accept client requests from client computers emulating those types of terminals.  
  
### To set up Host Integration Server for TN5250 access  
  
1.  Open **SNA Manager** console tree.  
  
2.  Install and configure a link service, if this has not been done.  
  
3.  Insert a connection to an AS/400 that the TN5250 clients will access. Configure the connection with Remote End as Peer System.  
  
4.  Configure a local LU and a remote LU for access to an AS/400, making sure the mode for the remote LU is QPCSUPP.  
  
5.  On the **File** menu, click **Save Configuration** to put the changes into effect.  
  
### To add and configure LUs for TN5250 service  
  
1. Before LUs can be added to the TN5250 service, you must first install a link service, add a connection to an AS/400 on this link service, and create local and remote LUs for accessing this AS/400.  
  
2. Right-click **TN5250**, point to **New**, and then click **TN5250 AS/400 Definition**.  
  
3. Configure the properties of this TN5250 AS/400 definition.  
  
    If you do not specify an IP address for an LU, the default value will allow any TN5250 client computer access to this LU.  
  
    Click **Help** for information on the property options.  
  
4. Click **OK** to close the **AS/400 Definition Properties** dialog box.  
  
5. On the **Action** menu, click **Save Configuration** to put the changes into effect.  
  
   Configuration changes are apparent only to users who establish a connection after the configuration changes are saved. Users who were connected at the time that the configuration changes were made will not be affected.  
  
   You can modify, delete, or add IP addresses and subnet masks to AS/400 definitions. If you want to change the configuration of multiple AS/400 definitions, you can only change properties such as display types, the IP address, and subnet mask that the AS/400 definitions have in common. You cannot change properties such as the local or remote LUs, because these values are unique for each AS/400 definition.  
  
   You can add new IP addresses and subnet masks to a range of AS/400 definitions. If the new IP address or subnet mask already exists on some of the AS/400 definitions, but not on others, the addition will occur without duplication in the ones that already have the IP address or subnet mask. You can also modify or delete the IP addresses that the AS/400 definitions have in common and that appear on the IP address list.  
  
#### To edit an AS/400 definition for TN5250 service  
  
1.  In the SNA Manager console tree, select the TN5250 service AS/400 definition that you want to view or modify, right-click, and then click **Properties**.  
  
#### To delete AS/400 definitions from TN5250 service  
  
1.  In the SNA Manager console tree, select the icon for the AS/400 definition that you want to delete.  
  
2.  Click **Delete**.  
  
3.  Click **Save** to save your configuration changes.  
  
> [!NOTE]
>  Configuration changes are apparent only to users who establish a connection after the configuration changes are saved. Users who were connected at the time that the configuration changes were made will not be affected.  
  
#### To start, pause, continue, and stop TN5250 service  
  
1. Right-click **TN5250**, and then click **Start** or **Stop**.  
  
    \- or -  
  
2. In the **Services** utility of the Windows **Administrative Tools**, select **TN5250 Service** and click **Start**, **Pause**, **Continue**, or **Stop**.  
  
   The TN5250 service is set to start manually by default. You can change this to automatic if you are not running either the TN5250 service on this server, or if you have configured the TCP ports for more than one of these services.  
  
   After TN5250 service has stopped, it can no longer be accessed. You may need to start the TN5250 service after you have paused or stopped it. TN5250 service can be restarted only on the local system.  
  
   Pausing allows you to prevent new users from establishing a connection with TN5250 service without disconnecting current users. You can then view session status in the Active TN5250 Sessions folder and notify connected users to disconnect from TN5250 service.  
  
   Before stopping TN5250 service, notify all connected users that they will be disconnected within a specified time period. Stop the service after expiration of your warning period.  
  
### Tips  
  
-   To start TN5250 service from a command prompt, type  
  
     **net start tn5250**  
  
-   To pause TN5250 service from a command prompt, type  
  
     **net pause tn5250**  
  
-   To continue TN5250 service from a command prompt, type  
  
     **net continue tn5250**  
  
-   To stop TN5250 service from a command prompt, type  
  
     **net stop tn5250**  
  
##### Pausing or removing TN5250 service  
  
1.  To pause TN5250 service, use the **Services** utility in Windows Control Panel.  
  
     Pausing TN5250 service allows you to notify connected users to disconnect from TN5250 service before you stop and remove the application.  
  
2.  To stop TN5250 service, use the **Services** utility in Windows Control Panel.  
  
3.  Open **Control Panel**, and then double-click **Add/Remove Programs**.  
  
4.  Click **Host Integration Server**, and then click **Change**. The **Add/Remove Programs** dialog box appears.  
  
5.  In the **Add/Remove Application** dialog box, click **Add/Remove**.  
  
6.  Click the **TN5250 Service** icon, and then click **Entire feature will be unavailable**.  
  
7.  Click **Continue**.  
  
> [!NOTE]
>  You can remove TN5250 service anytime you want to do so. However, removing TN5250 service deletes the TN5250 service files from your computer, including TN5250 service configuration data. To use TN5250 service again, you must run [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Setup to reinstall TN5250 service files.  
  
## See Also  
 [TN5250](../core/tn52501.md)