---
title: "Set up and install prerequisites for BizTalk Server 2016 | Microsoft Docs"
description: Step-by-step instructions to install and configure the required software and settings for BizTalk Server 2016
author: "MandiOhlinger"
manager: "anneta"

ms.prod: "biztalk-server"

ms.custom: ""
ms.date: "04/25/2018"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa70b621-903a-4cfa-9cb0-c6a82ed8f733
caps.latest.revision: 11
ms.author: "mandia"
---

# Set up and install prerequisites for BizTalk Server 2016
Set up the server, and install and configure the software prerequisites.

## Join the Administrators Group
To install and configure BizTalk Server, sign in to the server using an administrator account on the local computer. Add any user accounts that are administering the BizTalk Server to the local Administrators group:

1.	In the Start menu, open **Computer Management**.

    * Or, open **Administrative Tools**, and then select **Computer Management**.
    * Or, open **Server Manager**, select **Tools**, and then select **Computer Management**.
  
2.	Expand **Local Users and Groups**, and select **Groups**.
3.	Right-click the **Administrators** group, and select **Add to Group**. **Add** your accounts, and select **OK** to save your changes. 

## Change the computer name (optional)
If your computer name is longer than 15 characters, then BizTalk Server configuration fails. To change the computer name to less than 15 characters:

1.	In **Server Manager** > **Dashboard**, select **Local Server**. 
2.	In **Properties**, select the Computer name property to change it.
3. Restart the computer. 

**SEE ALSO** : Windows PowerShell [Rename-Computer](https://technet.microsoft.com/library/hh849792.aspx)

## Enable Network DTC Access
If BizTalk and SQL Server are installed on separate computers, then enable Network DTC Access on the BizTalk Server and the SQL Server. 

1. In the Start menu, open "dcomcnfg".

    * Or, open **Administrative Tools**, and then select **Component Services**.
    * Or, open **Server Manager**, select **Tools**, and then select **Component Services**.
  
2. Expand **Component Services**, expand **Computers**, expand **My Computer**,  and expand **Distributed Transaction Coordinator**.
3. Right-click **Local DTC**, and select **Properties**.
4. Go to the **Security** tab, and check the following:  
    * Network DTC Access
    * Allow Inbound
    * Allow Outbound
    * No Authentication Required
5. Select **OK**. If prompted to restart MS DTC, select **Yes**. 

For additional settings that may be needed, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).

## Configure Application Event Log (optional)

BizTalk Server setup keeps a record of events in the Application Event Log. Depending on the BizTalk Server features installed, the amount of space required in the log may exceed its limit. If the application event log runs out of space during the setup, the installation fails. Changing the Application Event Log settings prevents this failure.

1. In the Start menu, open **Event Viewer**:

    * Or, open **Administrative Tools**, and then select **Event Viewer**.
    * Or, open **Server Manager**, select **Tools**, and then select **Event Viewer**.
  
2. Expand **Windows Logs**, right-click **Application**, and then select **Properties**. 
3. To determine the available space, compare the **Log Size** and the **Maximum log size** properties. 

    * To add space, enter a higher number in **Maximum log size**.
    * To enable overwriting of old events when the log becomes full, select **Overwrite events as needed**.
    * To clear the log events, select **Clear log**.

4. Select **OK**.

## Edge can’t be opened (optional)

When using Edge, the following message displays:  
`Microsoft Edge can't be opened using the Built-in Administrator account. Sign in with a different account and try again.`

To allow Edge to open using the built-in administrator account:

1. In the Start menu, open **Local Security Policy**. Or, open **Server Manager**, select **Tools**, and then select **Local Security Policy**.
2.	Expand **Local Policies**, and select **Security Options**. 
3.	Go to the **User Account Control: Admin Approval Mode for the Built-in Administrator account** policy, and **Enable** the policy. 
4. Select **OK**, and restart your computer.

## Install Windows Updates

Be sure to install the latest critical Windows updates. 

1. On the Start menu, open **Windows Updates**, and check for updates. You can also open **Settings**, and select **Update and security**.
2. After installing updates, you may need to restart the computer.

## Enable IIS
BizTalk Server requires IIS for the following features:

- HTTP adapter
- SOAP adapter
- Windows SharePoint Services adapter
- Secure Sockets Layer (SSL) encryption
- BAM Portal
- EDI

IIS is included with the operating system as a **Role** or a **Feature**, depending on the OS. To install:

1. In the Start menu, open **Turn Windows Features on or off**. Or, open **Server Manager**, select **Manage**, and then select **Add roles and features**.
2. Select **Internet Information Services** or **Web Server (IIS)**. In addition to the default checked options, also select the following: 

    **Windows 10**
   - In **Web Management Tools**, also check:  
       - IIS 6 Management Compatibility
       - IIS 6 Management Console
       - IIS 6 Scripting Tools (Installs adsutil.vbs)
       - IIS Metabase and IIS 6 configuration compatibility
       - IIS Management Console
   - In **World Wide Web Services**, expand **Security** and also check:
       - Basic Authentication
       - Windows Authentication    

     **Windows Server**
   - In **Security**, also check: 
       - Basic Authentication
       - Windows Authentication    
   - In **Management Tools**, also check:  
       - IIS Management Console
       - IIS 6 Management Compatibility
       - IIS 6 Metabase compatibility
       - IIS 6 Management Console
       - IIS 6 Scripting Tools (Installs adsutil.vbs)

3. Continue with the installation, and restart the computer if prompted. 

**SEE ALSO** : Install IIS on [Windows 8 or Windows Server 2012](http://www.iis.net/learn/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012).


## Run 64-bit BAM portal (optional)
If you don't use the BAM portal, then you can skip this section. 

The BAM Portal runs in 32-bit mode. If you are using Internet Information Services (IIS) in a 64-bit environment, then set the application pool to run in 32-bit mode. 

#### Using adsutil.vbs
1.	Open a command prompt as administrator. 
2.	In the command prompt, type:  
    `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`
3. Select Enter.

#### Using IIS Manager
1. In the Start menu, open "inetmgr".
2.	Expand the computer name, and select **Application Pools**.
3.	Right-click **DefaultAppPool**, and select **Advanced Settings**. 
4.	Change the value of **Enable 32-bit Applications** to **True**. 
5.	Select **OK**.

## Install Windows Identity Foundation (WIF) (optional)
If you use the SharePoint Services adapter, BizTalk Server requires WIF. If you don't use the SharePoint Services adapter, you can skip this section.

Windows Identity Foundation is included with the operating system as a **Feature**.

1. In the Start menu, open **Turn Windows Features on or off**. Or, open **Server Manager**, select **Manage**, and then select **Add roles and features**.
2. Select **Windows Identity Foundation 3.5**, and continue with the installation. 
3. Restart the computer if prompted.

## Install & configure SMTP Server (optional)
If you use BAM Alerts, BizTalk Server requires SMTP Server. If you don't use BAM Alerts, you can skip this section.

SQL Server Database Mail uses an SMTP Server to send BAM Alerts. SMTP Server can be installed locally on the BizTalk Server or on another server with IIS installed. SMTP Server is not available on client operating systems, such as Windows 8.1 or Windows 10. 

SMTP Server is included with server operating systems as a **Feature**.

1. In the Start menu, open **Turn Windows Features on or off**. Or, open **Server Manager**, select **Manage**, and then select **Add roles and features**.
2. Select **SMTP Server**, and continue with the installation. 
3. Restart the computer if prompted.

## Install Excel 2016 or 2013 (optional)
If you use Business Activity Monitoring (BAM), BizTalk Server requires Excel. If you don't use BAM, you can skip this section.

The BAM Office Excel Workbook defines the business processes you want to monitor. You also use the BAM Excel Workbook to define the way business users see the data collected by BAM.

> [!IMPORTANT] 
> * BizTalk Server supports only 32-bit version of Microsoft Office. 
> * To successfully load BAM.xla into Excel, install **Visual Basic for Applications** (under **Office Shared Features**). Otherwise, you may get error: `This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`

#### Install Excel 2016

Office 2016 is installed using "Click-to-Run" or "C2R Installer". The C2R installation downloads and installs all programs within Office. For BAM, we only need Excel. To work around this, download and install the [Office 2016 Deployment Tool](https://www.microsoft.com/download/details.aspx?id=49117) to customize the C2R installer.

1. Download and install the [Office 2016 Deployment Tool](https://www.microsoft.com/download/details.aspx?id=49117).
2. In the folder with the Office 2016 Deployment Tool files you extracted, open the **configuration.xml** file with a text editor, such as notepad.
3. Replace the `<Configuration>` section with the following:  

    ```
    <Configuration>
    <Add SourcePath="D:\" OfficeClientEdition="32">
    <Product ID="O365ProPlusRetail" >
      <Language ID="en-us" />
      <ExcludeApp ID="Access" />
      <ExcludeApp ID="Groove" />
      <ExcludeApp ID="InfoPath" />
      <ExcludeApp ID="Lync" />
      <ExcludeApp ID="OneDrive" />
      <ExcludeApp ID="OneNote" />
      <ExcludeApp ID="Outlook" />
      <ExcludeApp ID="PowerPoint" />
      <ExcludeApp ID="Project" />
      <ExcludeApp ID="Publisher" />
      <ExcludeApp ID="SharePointDesigner" />
      <ExcludeApp ID="Visio" />
      <ExcludeApp ID="Word" />
    </Product>
    </Add>
    </Configuration>
    ```
	
  	Replace “SourcePath” with the location of your Office 2016 ISO file.
4. In the folder with the Office 2016 Deployment Tool files, hold down the **SHIFT** key, and right-click an empty area in the folder. Select **Open command window here**. 
5. Start the Excel installation by entering the following:  
  `setup.exe /configure configuration.xml`

    > [!TIP]
    > `setup.exe /download configuration.xml` downloads the required office setup files.
 
6. Select Excel, and continue with the installation. 
 
**SEE ALSO** : [Configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx) and [Install Office 2016 or 2013](https://support.office.com/article/Install-Office-on-your-PC-or-Mac-4414eaaf-0478-48be-9c42-23adc4716658)

#### Install Excel 2013
1. Run the Microsoft Office setup.
2. Select a **Custom Install**, and select Excel.
3. Continue with the installation.   

## Install Visual C++ redistributable package

Download and install the [Visual C++ redistributable package](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package). The 2013 version is required, even though Visual Studio 2015 is used.

The [Visual C++ downloads](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) lists all the available versions.

## Install Visual Studio 2015 (optional)
BizTalk Server requires Visual Studio to create BizTalk projects using the development tools. If this is a staging or production server, or you're not doing any BizTalk development, then skip this section.

Visual Studio Enterprise Edition is recommended, but Professional and Community editions are also supported. 

1. Run the Visual Studio setup as Administrator.
2. Select a **Default** installation. BizTalk Server does not require any of the optional features.

    > [!NOTE]
    > If you use Visual Studio for more than BizTalk projects, then select the **Custom** installation to install other features. Some commonly-used features include Microsoft Web Developer Tools, Microsoft Office Developer Tools, PowerShell Tools for Visual Studio, and ClickOnce Publishing Tools.
 
3. Continue with the installation, and restart your computer if prompted.

**SEE ALSO** : [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)

> [!IMPORTANT]
> - If you install Visual Studio before installing BizTalk Server, and then upgrade to Visual Studio Team Explorer, you may need to repair your BizTalk Server installation.
> - Visual Studio automatically installs Microsoft SQL Server Express; which is not used by BizTalk Server. Uninstall Microsoft SQL Server Express. You can also uninstall Microsoft SQL Server Compact.  
> - The BizTalk Server development tools are based on Visual Studio. At a minimum, install the Microsoft Visual C#® .NET component before you install the BizTalk Server Developer Tools and SDK.
> - The BizTalk Server runtime requires .NET Framework 4.6. If the Windows Communication Foundation (WCF) adapter or WCF Interceptor is installed, then .NET Framework 3.0 is required

#### Uninstall SQL Server Express
1. In the Start menu, open **Programs and Features**. Or, open the **Control Panel**, and select **Uninstall a program**.
2. Uninstall: 
    - Microsoft SQL Server 2014 Express LocalDb
    - Microsoft SQL Server Compact 4.0 SP1 x64 ENU
    - Microsoft SQL Server 2016 LocalDB (SQL Server 2016 Express LocalDB)
	
3. Continue with the uninstall, and restart your computer if prompted. 

## Install SQL Server 2016
BizTalk Server requires SQL Server. SQL Server can be installed on the same computer as BizTalk, or on a different computer. Most production environments install BizTalk and SQL on separate servers. 

> [!IMPORTANT]
> - SQL Server Express Edition is not recommended or supported. The Express edition does not include certain features needed by BizTalk Server.
> - BizTalk Server supports SQL Standard Edition. However, to use Business Activity Monitoring real-time aggregation (BAM RTA), install SQL Server Enterprise Edition. BAM real-time aggregation (RTA) is not supported in the Standard Edition of SQL Server.
> - To fully use the BizTalk Server SDK or deploy BizTalk Server applications from a Visual Studio, install the SQL Server Development Tools.
> - BizTalk Server supports all case-sensitive and case-insensitive SQL Server collations except for binary collations. Binary collations are not supported.

**For specific install steps, see** [Install SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup) or [Install SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx).

1. Start the SQL Server installation. 
2. During the Feature setup, select the following:
   - Database Engine Services
       - SQL Server Replication
       - R Services (in-Database) (**optional**; info at [SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services))
       - Full-Text and Semantic Extractions for Search
   - Analysis Services
   - Reporting Services - Native
   - Shared Features
       - Client Tools Connectivity
       - Integration Services

     > [!NOTE]
     > **SQL Server Data Tools** is not included in the default installation of SQL Server. It isn't required, but can be downloaded at [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt). Download [**SQL Server Management Studio (SSMS)**](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) that works with all supported versions of SQL Server, including Azure SQL Database. However, to connect to remote SSIS when using BAM, you need to install the same version of SSMS as the destination SSIS server. For example, [install SSMS 16.*x*](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-changelog-ssms?view=sql-server-2017#previous-ssms-releases) to install the related drivers to connect to SQL 2016 SSIS. SSMS 17.*x* cannot connect to SQL 2016 SSIS. You can have multiple versions of SSMS installed. 

3. Continue with the installation, and restart the computer if prompted.

## Disable Shared Memory

1. Open **SQL Server Configuration Manager**.
2. In SQL Server Configuration Manager, expand **SQL Server Network Configuration**, and then select **Protocols for MSSQLSERVER**.
3. Right-click **Shared Memory**, and then select **Disable**.
4. Select **SQL Server Services**, right-click SQL **Server (MSSQLSERVER)**, and then select **Stop**. After the service has stopped, right-click **SQL Server (MSSQLSERVER)**, and then select **Start**.
5. Close **SQL Server Configuration Manager**.

Typically, the Shared Memory protocol only impacts clients (BizTalk Server) that are installed on the same computer as SQL Server. Under certain stress conditions (such as clients accessing SQL Server from the same computer), the SQL Server Shared Memory protocol may lower BizTalk Server performance. Disabling the Shared Memory network protocol resolves this.

> [!TIP]
> If SQL Server Agent fails to start after disabling Shared Memory, then confirm 
> [ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) is installed.

## Install SQL XML 4
Required for BizTalk Server Runtime, Administrative Tools, and BAM. 

Download and install [SqlXml 4.0](https://www.microsoft.com/download/details.aspx?id=30403).

## Configure SQL Database Mail (optional)
If you use BAM Alerts, BizTalk Server requires SQL Server Database Mail. If you don't use BAM Alerts, then skip this section. 

**SEE ALSO** : More on [Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/database-mail).

> [!IMPORTANT]
> - You need to know the server name and TCP port number for the SMTP Server. If you installed IIS and SMTP Server on this same computer, then you use the local SMTP Server. If the SMTP server requires authentication, then have the user name and password ready.
> - The BAM portal and BAM Alerts are separate features. If you are using BAM Alerts, then SQL Server Database Mail is required. If you are not using BAM Alerts, then SQL Server Database Mail is not required.

**For specific configuration steps, see**: Configure [SQL Server 2016 Database Mail](https://docs.microsoft.com/sql/relational-databases/database-mail/configure-database-mail) or [SQL Server 2014 Database Mail](https://msdn.microsoft.com/library/hh245116(v=sql.120).aspx).

   
To send a test email: 
1.	Right-click **Database Mail**, and select **Send Test E-Mail**. 
2.	Enter a **To:** email address, and select **Send Test E-Mail**.  
 
If the **To:** recipient receives the email, then Database Mail is configured. 

## Install WinSCP (optional)
Required by the FTP adapter. If you don't use the FTP adapter, then skip this section. 

Download and install [WinSCP](http://winscp.net). 

## Next step
Install [BizTalk Server 2016](../install-and-config-guides/install-biztalk-server-2016.md).
