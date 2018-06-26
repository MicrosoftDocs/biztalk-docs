---
title: "Change Host Instance Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a35ca0c8-89b3-483a-b2fc-c8f43a8864d1
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update Host Instance Properties

## Overview
You can use the BizTalk Server Administration Console or Windows Management Instrumentation (WMI) to modify host instances. You can modify the service account running a host instance. You can also disable a host instance. For example, if you want to preserve the settings for a host instance and you do not want it to start, you can disable it. For more information about host instances, see [Host Instances](../core/host-instances.md).  
  
 Host instances of trusted hosts and host instances of non-trusted hosts cannot use the same service accounts. If you want to change the trust setting of a host instance and the host instance uses a service account that other host instances use, you can do one of the following:  
  
-   You can change the service account of the host instance for which you want to change the trust settings to a new service account.  
  
-   You can change the service account of the host instance to an existing service account that other host instances with the same trust setting use.  
  
-   You can delete the host instance, and re-create it with a different trust setting and service account.  
  
> [!CAUTION]
>  You must change the credentials for a host instance by updating the properties of the host instance. If you change the credentials of the corresponding service, the service account you specify for the host instance must be a member of the group on the host. Do not use the Services snap-in or the Computer Management console to change the credentials of host instance, otherwise the host instance may not function properly.  
  
> [!CAUTION]
>  If you change the credentials of a host instance, you must also change the corresponding SQL Server credentials. If you do not update the SQL Server credentials, the host instance will not function properly.  
  
 For information about using WMI to modify a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
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
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.  
  
3. In the details pane, right-click the host instance you want to modify, and then click **Properties**.  
  
4. In the **Host Instance Properties** dialog box, click **Configure** to modify the service account information.  
  
5. In the **Logon Credentials** dialog box, enter the account name and password of the account under which the host instance will run, and then click **OK**.  
  
6. In the **Host Instance Properties** dialog box, do the following, and then click **OK**:  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Host name**|Displays the name of the host associated with the selected server.|  
   |**Server**|Displays the server associated with the selected host.|  
   |**Logon**|Displays the account name of the new service account under which the host instance will run.|  
   |**Configure**|Click to display the **Logon Credentials** dialog box, where you can enter the account name and password of the account under which the host instance will run.|  
   |**Disable host instance from starting**|Select this check box to change the status of the selected host from enabled to disabled. Disabling a host instance is useful if you do not want the host instance to start, but you do want to preserve its settings.|  
  
## See Also  
 [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Add a Host Instance](../core/how-to-add-a-host-instance.md)   
 [Start a Host Instance](../core/how-to-start-a-host-instance.md)   
 [Stop a Host Instance](../core/how-to-stop-a-host-instance.md)   
 [Delete a Host Instance](../core/how-to-delete-a-host-instance.md)