---
title: "Add a Host Instance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98ba10a6-c5e7-4dec-98f1-4e6ba44c2851
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Add a Host Instance

## Overview
You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console or Windows Management Instrumentation (WMI) to add host instances. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you can only add a host instance to one server at a time. For more information about host instances, see [Host Instances](../core/host-instances.md). For information about using WMI to add a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 Adding a host instance maps the instance of a given host to an instance of BizTalk Server. If you have an existing host instance that you must repair, you can update the host instance properties. You must stop an existing host instance before you can add it again. For information about stopping a host instance, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).  
  
> [!NOTE]
>  If you want to create more that 26 host instances, you must follow the instructions in Knowledge Base article 184802, "User32.dll or Kernel32.dll Fails to Initialize," which is available at [http://go.microsoft.com/fwlink/?LinkId=26176](http://go.microsoft.com/fwlink/?LinkId=26176). If you require additional host instances after you apply the recommendations in this Knowledge Base article, you can try reducing the amount of memory available for each instance of the BTSNTSvc service. This will provide additional memory necessary to create more instances.  
  
> [!NOTE]
>  The service account will automatically be granted log on as service permissions on the server where the host instance is installed.  
  
## Prerequisites  
 To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.  
  
 In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:  
  
-   BAM Primary Import (BAMPrimaryImport)  
  
-   BizTalk Management (BizTalkMgmtDb)  
  
-   BizTalk MessageBox (BizTalkMsgBoxDb) (all)  
  
-   BizTalk Tracking (BizTalk DTADb)  
  
-   Rule Engine (BizTalkRuleEngineDb)  
  
> [!CAUTION]
>  We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script. This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.  
  
## Steps
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, and then click **Platform Settings**.  
  
3. Right-click **Host Instances**, click **New**, and then click **Host Instance**.  
  
4. In the **Host Instance Properties** dialog box, do the following, and then click **OK**:  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Host name**|Displays the name of the host associated with the selected server.|  
   |**Server**|Displays the server associated with the selected host.|  
   |**Logon**|Displays the account name of the new service account under which the host instance will run.|  
   |**Configure**|Click to display the **Logon Credentials** dialog box, where you can enter the account name and password of the account under which the host instance will run.|  
   |**Disable host instance from starting**|Select this check box to change the status of the selected host from enabled to disabled. Disabling a host instance is useful if you do not want the host instance to start, but you do want to preserve its settings.|  
  
   After you install a host instance, you must start it so that it can route messages to the MessageBox databases. For information about starting a host instance, see [How to Start a Host Instance](../core/how-to-start-a-host-instance.md).  
  
## Known Issues  
  
#### A BizTalk Host instance is created with a status of "Uninstall failed" if the designated BizTalk Server runtime computer is not available during host instance creation  
  
##### Problem  
 If the BizTalk Administration Console is installed on a machine that is remote to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computer, it is possible to attempt to create a host instance on the remote [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer even if the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer is unavailable.  
  
 If you attempt to create an instance of a BizTalk host on a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer that is unavailable, a dialog box with the following error message is displayed:  
  
 Installation of instace of host \<*host name*\> on server \<*server name*\> failed.  
  
 Additional information:  
  
 The RPC server is unavailable. (WinMgmt)  
  
 When you click OK to dismiss the dialog box, a dialog box with the following error message is displayed:  
  
 Cleaning up aborted installation of host \<*host name*\> on server \<*server name*\> failed.  
  
 Additional information:  
  
 A failure occurred when deleting the Windows NT service BTSSvc{*\<GUID\>*}. (WinMgmt)  
  
 When you click **OK** to dismiss this dialog box, the instance of the BizTalk host will be visible in the BizTalk Administration Console with a **Status** of **Uninstall failed**.  
  
##### Cause  
 When a host instance is created, an entry is made in the BizTalk Management database before the host instance is installed onto the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer. If the installation of the host instance onto the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer fails, the BizTalk Administration program will attempt to uninstall the host instance but since the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer is unavailable the uninstall fails as well.  
  
##### Resolution  
 If a BizTalk host instance is created in the BizTalk Admininstration Console with a status of **Uninstall failed**, delete the host instance and recreate the host instance after the designated BizTalk Server computer becomes available.  
  
> [!NOTE]
>  If a BizTalk host instance is created in the BizTalk Administration Console with a **Status** of **Uninstall failed** the host instance will not be functional even after the designated [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer becomes available again.  
  
## See Also  
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Start a Host Instance](../core/how-to-start-a-host-instance.md)   
 [Stop a Host Instance](../core/how-to-stop-a-host-instance.md)   
 [Delete a Host Instance](../core/how-to-delete-a-host-instance.md)   
 [Modify Host Instance Properties](../core/how-to-modify-host-instance-properties.md)