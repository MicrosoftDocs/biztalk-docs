---
title: "Install BizTalk Server 2013 and 2013 R2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b4665ea-6f2c-477f-98ec-1cebef05ad4a
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install BizTalk Server 2013 and 2013 R2
Lists the steps to install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## Before you get started

-   **Account names** – Use the default account names whenever possible. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup automatically enters the default accounts. If there are multiple [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groups within the Domain, change the account names to avoid conflicts. If you change the names, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports only \<*NetBIOS domain name*\>\\<*user*\> for service accounts and Windows groups.  
  
-   **Account names with BAM Management Web Service** – [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not support built-in accounts or accounts without passwords for the BAM Management Web Service User. The web service accesses the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database and these accounts may suggest a security threat.  
  
    > [!NOTE]
    >  Configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with these typs of accounts may succeed, but the BAM Management Web Service fails. Built-in accounts or accounts without passwords can be used for the BAM Application pool.  
  
-   **BizTalk Assembly Viewer** – Not supported on a 64-bit platform.  
  
-   **Install and Uninstall** – Uninstalling [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires manually deleting the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. If you are installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as a developer or evaluator, use a virtual machine. If you need to reinstall, you can easily roll back the virtual machine without having to uninstall and delete the databases.  
  
-   **32-bit and 64-bit computers** – There are few differences when installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on 32-bit or 64-bit computer. The installation and configuration covers 32-bit and 64-bit computers. Any differences are noted.  
  
-   **Workgroups** - Installing and configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the workgroup environment on a single computer is supported. SQL Server and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features and components are installed and configured on the same computer.  
  
-   **Terminal Server** – Installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] using Terminal Server running in application mode is not supported. See [KB 832027](http://support.microsoft.com/kb/832027).  
  
-   **BAM Portal**  - If the BAM portal is configured on a website used by applications that are running .NET Framework 2.0, then create a new website for the BAM portal:  
  
     [Create an IIS 7 web site](http://technet.microsoft.com/library/cc772350\(WS.10\).aspx)  
  
     [Create an IIS 8 web site](http://technet.microsoft.com/library/hh831515.aspx)  
  
     After creating the new website:  
  
    1.  Open **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration**.  
  
    2.  Configure the BAM portal and select the new website from the **BAM Portal Web Site** list.  
  
-   **Community Additions**: Read:  
  
     [Proactivity in BizTalk Server](http://msdn.microsoft.com/library/dn393929\(v=bts.10\).aspx)  
  
     [BizTalk Server 2013 R2: Installation and Configuration – Important considerations before set up the server (Part 1)](http://sandroaspbiztalkblog.wordpress.com/2015/01/04/biztalk-server-2013-r2-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/)  
  
##  <a name="BKMK_Install"></a> Install BizTalk Server  
  
1.  Close any open programs. Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installer as Administrator.  
  
2.  In **Start**, select **Install Microsoft BizTalk Server**.  
  
3.  In **Customer Information**, enter your user name, organization, product key, and then select **Next**.  
  
4.  In **License Agreement**, accept the license agreement, and select **Next**.  
  
5.  In **Customer Experience Improvement Program**, choose your participation preference, and then select **Next**.  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] participates in the Customer Experience Improvement Program. You choose to provide useful feedback to Microsoft regarding feature usage reporting functionality of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The data collected is anonymous and cannot be used to identify you. Microsoft collects feature usage statistics as part of this program. By participating in this program, you can help improve the reliability and performance of various features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. For more information about this program and its privacy policy, see [Microsoft BizTalk Server CEIP Privacy Policy](http://go.microsoft.com/fwlink/p/?LinkId=188553).  
  
6.  In **Component Installation**, review the available components, and select the ones you want to install:  

    |Feature|Description|  
    |-------------|-----------------|  
    |**Documentation**|Core documentation, tutorials, UI reference (F1 Help), programmer’s reference, and usage instructions for the SDK samples and utilities.|  
    |**Server Runtime**|The essential runtime services for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
    |**BizTalk EDI/AS2 Runtime**|Runtime services providing native support for Electronic Data Interchange (EDI) data exchange and Applicability Statement 2 (AS2) data transport messaging functionality. **Note:**  You can select this only if you selected the **Server Runtime** feature.|  
    |**Windows Communication Foundation (WCF) Adapter Runtime**|Adapters enabling [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to communicate with WCF-based applications. **Note:**  You can select this only if you selected the **Server Runtime** feature.|  
    |**Portal Components**|Portal components are a set of features used by the business analysts to communicate, collaborate, and reach decisions using business data.|  
    |**Business Activity Monitoring**|Also known as BAM, these are a set of features that gives business users a real-time view of their heterogeneous business processes, thereby enabling them to take important business decisions. **Note:**  You can select this only if you selected the **Portal Components** feature.|  
    |**Administrative Tools and Monitoring**|Components necessary to administer and monitor [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on both the local computer and a remote server.|  
    |**Windows Communication Foundation (WCF) Administration Tools**|Selecting this feature installs the administrative services for WCF components. **Note:**  You can select this only if you selected the **Administrative Tools and Monitoring** feature.|  
    |**Developer Tools and SDK**|Samples and utilities that enable rapid creation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions. This includes SDK samples and supporting documentation, schema and map designers, and Visual Studio project templates. **Important:**  You must install this component if you plan to do any development work. The Visual Studio extensions used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will not work without the **Developer Tools and SDK** component installed.|  
    |***Additional Software***||  
    |**Enterprise Single Sign-On (SSO) Administration Module**|The interface for managing SSO Affiliate Applications and their mappings.|  
    |**Enterprise Single Sign-On Master Secret Server**|The SSO server that stores the master secret. All other SSO servers in the system get the master secret from this server. The Master Secret Server is required in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.|  
    |**Business Rules Components**|Used for composing policies to be consumed by the Business Rules Engine.|  
    |**MQSeries Agent**|Provides communication between the BizTalk Adapter for MQSeries and MQSeries Server for Windows.|  
    |**Windows SharePoint Services Adapter Web Service**|**Deprecated**. Using an IIS web service installed on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer, the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] adapter processes incoming and outgoing documents through Microsoft SharePoint.<br /><br /> **Recommendation**: Do **not** install. By default, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the SharePoint Client Side Object Model (CSOM) Redistributable automatically installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]; as described at [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).|  
    |**BAM Alert Provider**|Configures BAM Alerts.<br /><br /> When using BAM Alerts with [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)] or [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] SP1, you must configure the Database Mail feature. SQL Server Notification Services cannot be used.|  
    |**BAM Client**|Client-side software enabling business users to work with BAM.|  
    |**BAM Eventing**|Interceptors for Windows Workflow Foundation and Windows Communication Foundation. Also includes the BAM Event API, which sends events to the BAM database from custom applications.|  
    |**Project Build Component**|A tool that enables you to build [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions without using Visual Studio.|  

7. Accept the default installation location, or select **Browse** to enter another location to install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Select **Next**.  
  
8.  If your computer is missing a prerequisite component, such as ADOMD.NET, Setup can install the redistributable prerequisites. You can either:  
  
    -   Select **Automatically install the redistributable prerequisites from the web**  
    
         OR  
  
    -   Select **Automatically install the redistributable prerequisites from a CAB file** if you have downloaded the CAB file. If you select this, you can then browse to the location of the CAB file.  
  
9.  In **Summary**, verify that the components are correct. To enable auto-logon after a system reboot, select **Set**, and enter your logon information. Auto-logon is enabled only for reboots during setup, and is disabled when setup is complete.  
  
10. Select **Install** to start the installation process.  
  
11. In **Microsoft Update Setup**, choose your preference, and select **Next**.  
  
12. In **Installation Completed**, uncheck **Launch [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration**, and then select **Finish**.  
  
## Additional  
  
-   When you installed SQL Server, SQL Server setup granted your logged-on account System Administrator rights. Since these rights are also required for installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must do one of the following:  
  
    -   Use the same account you used when you installed SQL Server.  
  
    -   Give the logged on account System Administrator rights.  
  
-   After you download the self-extracting EXE for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the installation guide is opened. The Setup.exe for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is at the same location as the installation guide.  
  
-   Instead of installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a physical computer, you can o configure a [!INCLUDE[winazure](../includes/winazure-md.md)] virtual machine with a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] image. See [Configuring BizTalk Server on an Azure VM](http://msdn.microsoft.com/library/azure/jj248689.aspx).  
  
-   For the steps to install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] using a command prompt, see [Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md).  
  
 
## See Also  
   
 [Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md)   
 [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)   
 [Appendix C: Redistributable CAB Files](../install-and-config-guides/appendix-c-redistributable-cab-files.md)   
 [Appendix D: Create the SMTP Server](../install-and-config-guides/appendix-d-create-the-smtp-server.md)