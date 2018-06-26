---
title: "Single-Server Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows SharePoint Services adapters, deploying"
  - "configuring [Windows SharePoint Services adapters], customizing"
  - "deploying, Windows SharePoint Services adapters"
  - "Windows SharePoint Services adapters, installing"
  - "Windows SharePoint Services adapters, configuring"
  - "configuring [Windows SharePoint Services adapters], single-server deployment"
  - "Windows SharePoint Services adapters, single-server deployment"
ms.assetid: 94ba8241-9a30-46ca-b962-721e2d00f420
caps.latest.revision: 25
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single-Server Deployment
This topic discusses single-server setup and deployment considerations for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter for Windows SharePoint Services.  
  
## Installing the Windows SharePoint Services adapter in a single-server deployment  
 Selecting the Windows SharePoint Service adapter Web service component installs the necessary software for the Windows SharePoint Services adapter to process incoming and outgoing documents through Windows SharePoint Services. This Web service must be installed on the server where Windows SharePoint Services is installed. The adapter Web service can handle multiple SharePoint sites including the Web site that hosts Business Activity Services (BAS), regardless of whether they are on the same IIS site or on different IIS sites.  
  
 The Windows SharePoint Services adapter has three components:  
  
- Runtime components  
  
- Design time components  
  
- Adapter Web service  
  
  The adapter runtime is installed and configured automatically by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime feature. The adapter design time components are installed and configured with the other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features. You interact with the design time components by creating Windows SharePoint Services ports through tools that are included in the Administration Tools, Developer Tools, and SDK or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime features. You cannot customize any configuration options for runtime and design time components. You can customize only the Windows SharePoint Service adapter Web service options.  
  
  Only members of the SharePoint Enabled Hosts group have permissions to invoke the adapter Web service. For more information about the Windows SharePoint Services permissions needed by the Windows SharePoint Services adapter runtime, see the security section in [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).  
  
> [!NOTE]
>  The Windows SharePoint Services adapter Web service component will be automatically selected if you choose to install BAS.  
  
#### To install the Windows SharePoint Services adapter  
  
1.  Install BizTalk Server. For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
2.  On the **Component Installation** screen, under **Available Components**, under **Additional Software**, select **Windows SharePoint Services Adapter Web service**.  
  
## Configuring the Windows SharePoint Services adapter Web service in a single-server deployment  
 You can configure the Windows SharePoint Services adapter using either a basic configuration or a custom configuration. For more information about these tools, see [Configuration Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).  
  
### Using a basic configuration  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] allows you to configure the server by using default settings. The default settings for the server are configured using the database server name, user name, and password that you enter into the configuration wizard. When you configure the Windows SharePoint Services adapter Web service using a basic configuration, the following happens:  
  
-   The SharePoint Enabled Hosts Windows group is created.  
  
-   The Default Web Site is used to host the Windows SharePoint Services Adapter  
  
-   The BTSSharePointAdapterWSAppPool application pool is created and configured to run under the account that is also used to run the Windows SharePoint Services application pool.  
  
-   The BTSharePointAdapterWS virtual application is created and configured to run in the BTSSharePointAdapterWSAppPool application pool  
  
> [!NOTE]
>  If this virtual directory already exists, configuration will not update the properties in the metabase. You must delete the virtual directory, and run configuration again.  
  
- The BTSharePointAdapterWS virtual application contains the Web service  
  
  For more information about basic configuration, see [Basic Configuration](http://msdn.microsoft.com/library/abdf3eb5-9779-47ff-bc97-2209eb4b12f5).  
  
### Using a custom configuration  
 The BizTalk Server Configuration provides a high-level analysis of the configuration state of the features you have installed on the local computer. The tool allows you to configure and unconfigure features, configure security settings, and import and export configurations from other computers.  
  
 Use the **Windows SharePoint Services Adapter Web Service** page to configure the Windows SharePoint Services adapter on this computer. The following table lists the configuration options.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Enable Windows SharePoint Services Adapter on this computer**|Select **Enable Windows SharePoint Services Adapter on this computer** to enable the adapter on this computer.|  
|**Windows group**|The **Windows group** list provides a view that you can edit of the BizTalk SharePoint Adapter Enabled Hosts Windows group.|  
|**Windows SharePoint Services Adapter Web site**|Select the Web site that will host the Windows SharePoint Service adapter Web service.|  
  
 When you configure the Windows SharePoint Services adapter using a custom configuration, the following happens:  
  
-   The SharePoint Enabled Hosts Windows group is created by default unless you specify another Windows group  
  
-   The Default Web Site is used to host the Windows SharePoint Services adapter unless you specify another Web site  
  
-   The BTSSharePointAdapterWSAppPool application pool is created and configured to run under the account that is also used to run the Windows SharePoint Services application pool  
  
-   The BTSharePointAdapterWS virtual application is created and configured to run in the BTSSharePointAdapterWSAppPool application pool  
  
> [!NOTE]
>  If this virtual directory already exists, configuration will not update the properties in the metabase. You must delete the virtual directory, and run configuration again.  
  
- The BTSharePointAdapterWS virtual application contains the Web service  
  
  For more information about the custom configuration manager, see [Import and Export BizTalk Server Configuration](../install-and-config-guides/import-and-export-biztalk-server-configuration.md).  
  
##### To configure the Windows SharePoint Services adapter by using a custom configuration  
  
1.  In the **BizTalk Server Configuration**, select the **SharePoint adapter** node.  
  
2.  Select **Enable Windows SharePoint Services Adapter on this computer**.  
  
3.  Under **Windows Group**, select the Windows group you will be using for the Windows SharePoint Services adapter. By default, this is SharePoint Enabled Hosts.  
  
4.  In the **Windows SharePoint Services Adapter Web Site** drop-down box, select the Web site where the adapter components will be installed. By default, this is the Default Web Site.  
  
5.  Click **Apply Configuration**.  
  
## Considerations for a single-server deployment  
 When you set up and deploy the Windows SharePoint Services adapter in a single-server environment, consider the following:  
  
- Add the BizTalk Service account to the SharePoint Enabled Hosts Windows group on that server.  
  
- Add the SharePoint Enabled Hosts group to the SharePoint Contributors role using the SharePoint Central Administration tool.  
  
- On [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], the identity under which the SharePoint Adapter Web Service runs needs the following permissions:  
  
   **Read** permissions on the **Program Files\Microsoft BizTalk Server \<version\>\Business Activity Services\BTSharePointV3AdapterWS** folder. If using a 64-bit version of Windows and BizTalk Server, permissions need to be set on the **Program Files (x86)\Microsoft BizTalk Server \<version\>\Business Activity Services\BTSharePointV3AdapterWS**  
  
   **Read** permission on the following registry key: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**.  
  
   Logon permissions on the SQL Server that contains the Sharepoint databases.  
  
   A member of the **Public** and **WSS_Content_Application_Pools** roles within the SharePoint configuration database.  
  
   A member of the **Public** and **db owner** roles within the SharePoint content database.  
  
- The Web site that you install the Web service on must be extended as a SharePoint Services Web site.  
  
- You can install and configure the Windows SharePoint Services adapter using silent installation. For more information, see [Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md).  
  
## See Also  
 [Windows SharePoint Services Adapter](../core/windows-sharepoint-services-adapter.md)   
 [Multiserver Deployment](../core/multiserver-deployment.md)