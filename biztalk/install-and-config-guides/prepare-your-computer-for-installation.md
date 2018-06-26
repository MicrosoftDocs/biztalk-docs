---
title: "Prepare Your Computer for Installation | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2016"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53df7a2f-638b-4921-a97f-736760248526
caps.latest.revision: 32
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Prepare Your Computer for Installation
This topic lists the steps to prepare your computer by installing and configuring all software prerequisites, and then creating accounts and setting permissions.  

> [!TIP] 
> An integration MVP prepared a very detailed step-by-step guide to install the prerequisites, and BizTalk Server:  [BizTalk 2013 Installation and Configuration part 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/).  
> 
> Some steps are not recommended by Microsoft, such as disabling User Access Control (UAC) or Windows Firewall. 
  
> [!IMPORTANT]
>  Complete these tasks in the order listed.  
  
##  <a name="BKMK_InstUpdates"></a> Install Windows Updates  
  
- **Windows 7**: Click Start. In the **Search** text box, type **Windows Update**.  
  
- **Windows 8.1, Windows Server 2012, and Windows Server 2012 R2**: Click the Windows button on the keyboard and type **Windows Update**. From the search results, click **Windows Update**.  
  
  After installing updates, you may need to restart the computer.  
  
##  <a name="BKMK_IIS"></a> Enable Internet Information Services  
 Microsoft Internet Information Services (IIS) provides a Web application infrastructure for many BizTalk Server features, including:  
  
-   HTTP adapter  
  
-   SOAP adapter  
  
-   Windows SharePoint Services adapter  
  
-   Secure Sockets Layer (SSL) encryption  
  
-   BAM Portal  
  
#### Install IIS

For the specific install steps, see: 

[Install IIS (Windows 8 and Windows Server 2012)](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012)

[Install IIS (Windows 7 and Windows Vista)](https://docs.microsoft.com/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)


When you install IIS, in addition to the default checked options, also check the following:  
  
- **Web Management Tools**: Also check:  
  
    - IIS 6 Management Compatibility:  
  
        - IIS 6 Management Console  
  
        - IIS Metabase and IIS 6 configuration compatibility  
  
    - IIS Management Console  
  
- **World Wide Web Services**: Expand **Security** and also select:  
  
    - Basic Authentication  
  
    - Windows Authentication  

Also consider the following:  
  
- **.Net Framework 3.5 Features**: .NET Framework 4.5 and .NET Framework 3.5 can be used to develop .Net applications involving the BizTalk Adapter Pack. Typically, **.NET Framework 4.5 Features** is already installed. If you will use .NET Framework 3.5 to create applications on this computer, then **.Net Framework 3.5 Features** can also be installed.  
  
- **Message Queuing**: If you are using the MSMQ adapter, you can create a local MSMQ store by checking **Message Queuing**.  
  
- **SMTP Server**: If you are using the SMTP adapter, you can create a local SMTP Server by checking **SMTP Server**.  
  
- **Windows Identity Foundation 3.5**: Windows Identity Foundation (WIF) is required by the SharePoint adapter when using the CSOM installation option. [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the CSOM installation option for the SharePoint adapter.    
  
 
##  <a name="BKMK_XLS"></a> Install Microsoft Office Excel  
  
1. Run the Microsoft Office setup.  
  
2. When you reach the **Type of Installation** screen, select **Custom Install**, and then select **Next**.  
  
3. On the **Custom Setup** screen, select **Excel**, and then select **Next**.  
  
4. Select **Install**.  
  
5. In **Setup Completed**, select **Finish**.  
  
   **Additional**  
  
-   BizTalk Server supports only 32-bit version of Microsoft Office.  
  
-   Microsoft Office Excel is required by Business Activity Monitoring (BAM) in BizTalk Server. The BAM Office Excel Workbook defines the business processes you want to monitor. You also use the BAM Excel Workbook to define the way business users see the data collected by BAM.  
  
-   To successfully load BAM.xla into Excel, install **Visual Basic for Applications** under **Office Shared Features**. Otherwise, you may get error “This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.”  
  
##  <a name="BKMK_VS"></a> Install Visual Studio  
  
1. Run the Visual Studio setup as Administrator.  
  
2. Accept the license agreement and click **Next**.  
  
3. In **Optional features to install**, select the options you need and then select **Install**. BizTalk Server does not require any of the optional features.  
  
4. On the **Finish** page, close the window or click **Launch** to open Visual Studio.  
  
   **Additional**  
  
-   If you install Visual Studio before installing BizTalk Server, and then upgrade to Visual Studio Team Explorer, you may need to repair your BizTalk Server installation from the **Control Panel** / **Programs** option.  
  
-   Visual Studio automatically installs Microsoft SQL Server Express; which is not used by BizTalk Server. As a best practice, uninstall Microsoft SQL Server Express.  
  
-   The BizTalk Server development tools are based on Visual Studio. At a minimum, you must install the Microsoft Visual C#® .NET component of Visual Studio before you install the BizTalk Server**Developer Tools and SDK**.  
  
-   Visual Studio is *not* required if you are installing BizTalk Server on a production computer (runtime only), on which no application development or debugging is required.  
  
-   The BizTalk Server runtime requires .NET Framework 4.5. The .NET Framework 3.0 is required if the Windows Communication Foundation (WCF) adapter or WCF Interceptor is installed.  
  
##  <a name="BKMK_SQL"></a> Install SQL Server  
 Install [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)  
  
 Install [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)  
  
 Install [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)  
  
 When you install SQL Server, select the following features:  
  
- Database Engine Services  
  
  -   SQL Server Replication  
  
  -   Full-Text Search  
  
- Analysis Services  
  
- Reporting Services  
  
- Shared Features  
  
  -   SQL Server Data Tools (SQL Server 2014 / SQL Server 2012) or Business Intelligence Development Studio (SQL Server 2008 R2)  
  
       [Download SQL Server 2014 Data Tools](http://www.microsoft.com/download/details.aspx?id=42313)  
  
  -   Client Tools Connectivity  
  
  -   Integration Services  
  
  -   Management Tools - Basic  
  
      -   Management Tools - Complete  
  
  **Additional**  
  
- BizTalk Server supports all case-sensitive and case-insensitive SQL Server collations except for binary collations. Binary collations are not supported.  
  
- For optimal performance, Microsoft recommends using the Enterprise Edition of SQL Server. See [SQL Server 2008 R2 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx), [SQL Server 2012 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx), or [SQL Server 2014 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx).  
  
- Service packs and Windows Updates are supported and should be installed.  
  
- When BizTalk Server and SQL Server are on separate computers, Distributed Transaction Coordinator (MS DTC) handles the transactions between the computers. The SQL Server AlwaysOn feature does not support MSDTC transactions. The SQL Server AlwaysOn feature is not supported.  
  
##  <a name="BKMK_MQSeries"></a> Install MQSeries Prerequisites  
 **MQSeries adapter**: Automatically installed with the BizTalk Server installation.  
  
 **MQSeries Client (MQSC) adapter**:  
  
1. Run the Host Integration Server (HIS) installation  
  
2. In component installation, expand **BizTalk Adapters**.  
  
3. Select **BizTalk Adapter for WebSphere MQ (Client-Based)**.  
  
   **Supported IBM WebSphere MQ versions**:  
  
-   IBM WebSphere MQ 6.0.2.12 and later  
  
-   IBM WebSphere MQ 7.0.1.9 and later  
  
-   IBM WebSphere MQ 7.1.0.5 and later  
  
-   IBM WebSphere MQ 7.5.0.3 and later  
  
-   IBM WebSphere MQ 8 (limited to runtime; no administration APIs)  
  
     MQ version 8 support is included with [Host Integration Server CU3](https://support.microsoft.com/kb/3019572).  
  
> [!NOTE]
>  If a specific WebSphere MQ version is not listed, like MQ 5.x, then it is not supported with this BizTalk Server version.  
  
 **Additional**  
  
- As a best practice, always install the latest WebSphere MQ fix pack. See [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037).  
  
- If IBM WebSphere MQ is installed on a non-Windows computer, install the **MQSAgent COM+ application** (MQSConfigWiz.exe) and **MQSeries Server for Windows** on the same computer. If IBM WebSphere MQ is installed on a Windows computer, then the **MQSAgent COM+ application** and **MQSeries Server for Windows** program are not used or needed.  
  
   **MQSConfigWiz.exe** is included in the BizTalk Server installation files.  
  
   **MQSeries Server for Windows** is not a Microsoft program and must be obtained with your IBM WebSphere MQ program.  
  
- [MQSeries Adapter](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx) provides more information on the MQSeries adapter, including configuring the different components. [BizTalk Server: MQSeries and MQSeries Client (MQSC) adapters](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) provides additional details on the MQSeries and MQSC adapters.  
  
- IBM WebSphere is not a Microsoft product and is not supported by Microsoft. Microsoft makes no guarantees about the suitability of this program. For more information about IBM WebSphere MQ, including download instructions, see www.ibm.com.  
  
##  <a name="BKMK_BAMAlerts"></a> BAM Alerts  
 BAM Alerts with SQL Server 2012 and newer versions use Database Mail in SQL Server. BAM Alerts with SQL Server 2008 R2 and older versions use SQL Notification Services. Before installing or configuring BAM Alerts, you must configure the Notification Services or Database Mail in SQL Server.  
  
###  <a name="BKMK_DBMail"></a> BAM Alerts using SQL Server 2012/2014  
 Configure [SQL Server 2012 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx).  
  
 Configure [SQL Server 2014 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx).  
  
 **Additional**  
  
-   Database Mail uses an SMTP server to send the BAM Alerts. SMTP Server can be installed locally on the BizTalk Server or on another IIS server. [Appendix D: Create the SMTP Server](../install-and-config-guides/appendix-d-create-the-smtp-server.md) lists the steps to install and configure a SMTP Server.  
  
###  <a name="BKMK_SSNS"></a> BAM Alerts using SQL Server 2008 R2 – Install SQL Server 2005 Notification Services  
  
1. Go to [Feature Pack for Microsoft SQL Server 2005 SP4](http://go.microsoft.com/fwlink/p/?LinkId=286285).  
  
2. Download and install the appropriate platform package for the following components:  
  
    **Microsoft SQL Server Native Client**  
  
   - HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi>" X86 Package (sqlncli.msi)  
  
   - HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi>" X64 Package (sqlncli_x64.msi)  
  
     **Microsoft SQL Server 2005 Management Objects Collection**  
  
   - HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi>" X86 Package (SQLServer2005_XMO.msi)  
  
   - HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi>" X64 Package (SQLServer2005_XMO_x64.msi)  
  
     **Microsoft SQL Server 2005 Notification Services Client Components**  
  
   - HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi>" X86 Package (SQLServer2005_NS.msi)  
  
   - HYPERLINK "<http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi>" X64 Package (SQLServer2005_NS_x64.msi)  
  
   **Additional**  
  
-   SQL Notification Services does not need to be configured; only installed on the BizTalk Server.  
  
##  <a name="BKMK_WIF"></a> Windows Identity Foundation  
  
|                                                              |                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Windows 8.1, Windows Server 2012, and Windows Server 2012 R2 |                                Windows Identity Foundation is included with the operating system as a Feature in **Turn Windows features on or off**.                                |
|                      Windows Vista SP1                       | Download available at [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) HYPERLINK "<http://www.microsoft.com/download/details.aspx?id=17331>" . |
  
 **Additional**  
  
-   Windows Identity Foundation (WIF) is required for the SharePoint adapter or SharePoint Online when used with SharePoint Client Side Object Model (CSOM). Specifically:  
  
    |Installation Option|WIF Required|  
    |-------------------------|------------------|  
    |SharePoint Adapter with CSOM|Yes|  
    |SharePoint Online with CSOM|Yes|  
    |SharePoint Adapter Web Service (deprecated)|No|  
    |No SharePoint|No|  
  
-   [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) provides specific information on the SharePoint installation options.  
  
##  <a name="BKMK_WSS"></a> Install and Configure Microsoft SharePoint  
 Install [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)  
  
 Install [SharePoint Online Service](http://technet.microsoft.com/library/jj819267.aspx)  
  
 Install [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)  
  
 Install [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)  
  
 **Additional**  
  
-   If you are installing SharePoint, you must do so before continuing with the remaining BizTalk Server prerequisites.  
  
-   Installing and configuring SharePoint consists of the following procedures:  
  
    -   Install SharePoint  
  
    -   Configure SharePoint  
  
    -   Extend the default Web site as a virtual server  
  
-   [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the SharePoint adapter installation options for BizTalk Server.  
  
-   When using the SharePoint adapter, it is recommended to install the new CSOM option instead of the SharePoint Service Web Service; described at [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).  
  
##  <a name="BKMK_SharedMem"></a> Disable the Shared Memory Protocol  
  
1. Open **SQL Server Configuration Manager**.  
  
2. In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, and then select **Protocols for MSSQLSERVER**.  
  
3. Right-click **Shared Memory**, and then select **Disable**.  
  
4. Select **SQL Server Services**, right-click **SQL Server (MSSQLSERVER)**, and then select **Stop**. After the service has stopped, right-click **SQL Server (MSSQLSERVER)** again, and then select **Start**.  
  
5. Close **SQL Server Configuration Manager**.  
  
   **Additional**  
  
-   Under certain stress conditions (such as clients accessing SQL Server from the same computer), the SQL Server Shared Memory protocol may lower BizTalk Server performance. You can resolve this behavior by disabling the Shared Memory network protocol in SQL Server Network Configuration.  
  
-   ReplaceThisText  
  
##  <a name="BKMK_LocalAdmin"></a> Join the Local Administrators Group  
 **Windows Server 2012** : [Windows Server 2012: How to Add an Account to a Local Administrator Group](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)  
  
 **Windows 8.1**: To open Local Users and Groups on Windows 8, click the Windows button on the keyboard and type **groups**. In the Search window, click **Settings**. In the Results window, click **Edit local users and groups**. Click **Groups** and then double-click Administrators to add an account.  
  
 **Windows 7 SP1**: Click Start. In the **Search** text box, type **Computer Management**, and click it to open. Expand **Local Users and Groups**, click **Groups**, and then double-click Administrators to add an account.  
  
 **Additional**  
  
-   You must be a member of the local Administrators group to install and configure BizTalk Server.  
  
##  <a name="BKMK_AppLog"></a> Configure the Application Event Log  
  
1. Open **Event Viewer**:  
  
    **Windows Server 2012** : Click the Windows button on the keyboard and type **Event Viewer**. In the Results window, click **Event Viewer**.  
  
    **Windows 8.1**: Click the Windows button on the keyboard and type **Event Viewer**. In the Search window, click **Settings**. In the Results window, click **View event logs**.  
  
    **Windows 7 SP1**: Click Start. In the **Search** text box, type **Event Viewer**, and click it to open.  
  
2. Expand **Windows Logs**, right-click **Application**, and then click **Properties**. In **Log Properties**:  
  
   -   To determine the available space, compare the **Log Size** and the **Maximum log size** properties.  
  
   -   To provide more space, enter a higher number in **Maximum log size**.  
  
   -   To enable overwriting of old events when the log becomes full, select **Overwrite events as needed**.  
  
   -   To clear the log events, select **Clear log**.  
  
3. Click **OK** to close the **Event Viewer**.  
  
   **Additional**  
  
-   BizTalk Server setup keeps a record of events in the Application Event Log. Depending on the BizTalk Server features installed, the amount of space required in the log may exceed its limit. If the application event log runs out of space during BizTalk Server setup, the installation fails. Changing the Application Event Log settings prevents this failure.  
  
## Next  
 [Choose BizTalk Server Features and Components](http://msdn.microsoft.com/library/b8c43fcf-9e5c-48ba-830b-13a5177e30f0)  
  
## See Also  
 [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md)   
 [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)   
 [Appendix C: Redistributable CAB Files](../install-and-config-guides/appendix-c-redistributable-cab-files.md)   
 [Appendix D: Create the SMTP Server](../install-and-config-guides/appendix-d-create-the-smtp-server.md)
