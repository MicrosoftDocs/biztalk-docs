---
title: "How to Update the Runtime Computers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 576a7065-04b6-436c-acf9-28c8d6e40107
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Update the Runtime Computers
The destination system [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers are configured with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard as part of the production BizTalk group running in the production environment. When the production BizTalk group is restored in the disaster recovery environment, settings must be updated on each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computer so that it points to the disaster recovery [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s) when it attempts to connect to the restored production BizTalk group. After the BizTalk group is restored in the destination system, use the following procedure to update the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers.  
  
### To update the BizTalk Server runtime computers  
  
1. Copy the edited SampleUpdateInfo.xml file to the \Program Files\Microsoft BizTalk Server\Schema\Restore directory on every 32 bit BizTalk server or to the \Program Files (x86)\Microsoft BizTalk Server\Bins32\Schema\Restore directory on every 64 bit BizTalk server in the destination system.  
  
2. On each BizTalk server, open a command prompt. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
   > [!NOTE]  
   >  On 64-bit computers, you must open a 64-bit command prompt.  
  
3. At the command-prompt, navigate to \Program Files\Microsoft BizTalk Server\Schema\Restore (on 32 bit computers) or to \Program Files (x86)\Microsoft BizTalk Server\Bins32\Schema\Restore (on 64 bit computers) and type this command:  
  
   ```  
   cscript UpdateRegistry.vbs SampleUpdateInfo.xml  
   ```  
  
4. Enable and restart all BizTalk Host instances and all other BizTalk Services on the BizTalk servers in the destination system.  
  
5. Restart WMI on each BizTalk server in the destination system. Click **Start**, click **Run**, type **services.msc**, and then click **OK**. In the **Services** MMC snap-in, right-click **Windows Management Instrumentation** and select **Restart**.  
  
6. On each BizTalk server, open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **BizTalk Group**, and then select **Remove**.  
  
7. Right-click **BizTalk Server 2010 Administration**, select **Connect to Existing Group**, select the SQL Server database instance and database name that corresponds to the BizTalk Management database for the BizTalk group, and then click **OK**.  
  
   > [!NOTE]
   >  After updating the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers, you may also need to update the **SSO Server name** as displayed in the **Group Properties** dialog box available in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. To update the **SSO Server name**, launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click to expand [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration, right-click the **BizTalk Group** node and select **Properties** to display the **General** tab of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. Then, in the **SSO Server name** textbox, enter the name of the Enterprise Single Sign-On server that this computer will use to access the configuration information for the adapters and click **OK**. This is the name of the SSO server used to connect to the SSO database.  
  
8. Restart the following Windows services on each BizTalk runtime server:  
  
   -   Enterprise SSO Service  
  
   -   Rule Engine Update Service  
  
   -   BizTalk Host Instances  
  
## See Also  
 [Recovering the Runtime Computers](../technical-guides/recovering-the-runtime-computers.md)