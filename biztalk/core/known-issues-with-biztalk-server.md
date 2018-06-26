---
title: "Known Issues with BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1aa5fb60-e8db-4cd2-88be-3c71b7b1d44d
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with BizTalk Server
This topic lists some known issues with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## DTC Firewall Rules  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are installed on separate computers, Distributed Transaction Coordinator (MS DTC) handles the transactions between the computers. As a result, enable the DTC ports within your firewall rules on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers.  
  
 When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the following errors can occur when the DTC ports are not enabled in the firewall:  
  
 **WMI Error occurred during database creation; attempt to rollback and delete the partially created database'SQLServerName\BizTalkMsgBoxDb'**  
  
 **WMI error description is generated: Exception of type 'System.EnterpriseServices.TransactionProxyException' was thrown.**  
  
 The following links provide more information:  
  
 [Ports for the Administration Server](http://go.microsoft.com/fwlink/p/?LinkID=275568)  
  
 [Post-installation Steps for BizTalk Server 2013 and 2013 R2](../install-and-config-guides/post-installation-steps-for-biztalk-server-2013-and-2013-r2.md)  
  
##  <a name="BKMK_BAM"></a> Business Activity Monitoring  
 This section lists the known issues with the Business Activity Monitoring (BAM) module.  
  
### BAM definition deployment fails due to a SQL login error  
 While deploying BAM definition, the operation might fail due to a login error with error code 42000.  
  
```  
...  
Deploying Activity... Done.   
Deploying View... ERROR: The BAM deployment failed.   
Server: The current operation was cancelled because another operation in the transaction failed.   
OLE DB error: OLE DB or ODBC error: Login failed for user <username>.; 42000.   
…  
```  
  
 To fix this issue, make sure the SQL Analysis Service logon account has permissions on all databases related to BAM.  
  
### BAM configuration might result in warnings related to the BAM Analysis logon account  
 BAM configuration adds the permissions for BAM Analysis logon account in all the databases related to BAM to be able to access them. However, the configuration might fail to do so and give a warning if any of the following prerequisites is not met:  
  
- The user under which the BAM configuration is run should be an administrator on the computer where Analysis Service is installed.  
  
- Remote administration through firewall must be allowed on that computer.  
  
- You might also get a warning if the BAM Analysis logon account is an administrator for the SQL Server where the BAM-related databases are installed. You can ignore the warning and move ahead.  
  
  **Workaround** – You must manually add the permission for the BAM Analysis logon account on all databases related to BAM.  
  
### BAM Portal Compatibility with Internet Explorer 10  
 To use the BAM Portal with Internet Explorer 10, you must always use the browser in Compatibility mode.  
  
### Receiving notification e-mails even after the Alert Host service is stopped  
 If you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], you must configure the Database Mail feature in SQL Server if you want to use BAM Alerts. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses an Alert Host service in conjunction with the Database Mail feature to send notification alerts. The Alert Host service, after processing the notifications, passes on the notification workload to the Database Mail component in SQL Server. So, even if you stop the Alert Host service, you might still get a few notifications for events that were processed by the Alert Host service but not by the Database Mail component.  
  
### Configuring tracing for BAM Alerts  
 If you are using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], and you want to enable diagnostic tracing for BAM Alerts, you must do so by creating a config file for the BAM Alerts host. You must name the file as **BAMAlerts.exe.config** and copy it to the same location as the EXE (**BAMAlerts.exe**), which is at \Program Files\Microsoft BizTalk Server\Tracking\\.  
  
 A sample config file looks like the following. This file logs **Information** level details to the Event Viewer.  
  
```  
<configuration>  
  <system.diagnostics>  
    <switches>  
      <add name="LogEventProvider" value="Info"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
##  <a name="BKMK_Upgrade"></a> Issues While Using BizTalk Server with SQL Server 2012  
 While using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] you can set the **Remote Login Timeout** value in SQL Server to 20 seconds. If you don’t do so, you might encounter errors in stress conditions. For instructions on how to set the Remote Login Timeout value in [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], see [http://msdn.microsoft.com/library/ms175136.aspx](http://msdn.microsoft.com/library/ms175136.aspx)  
  
##  <a name="BKMK_Adapters"></a> Issues with Adapters  
 This section lists the known issues with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters.  
  
### Dynamic port may fail while using the Windows SharePoint Services (WSS) adapter  
 A dynamic port using the WSS adapter may fail with the following error:  
  
```  
Error details: The Windows SharePoint Services site was not found. The URL "http://server:443/site" points to a SharePoint object for which there is no Windows SharePoint Services site.  
```  
  
 **Workarounds**:  
  
-   In the port configuration, for the site URL, include the port number as well. For example, `http://server:80/site`.  
  
-   Enable the **Windows Identity Foundation 3.5** feature.  
  
-   Confirm the account running the BizTalk host has access to SharePoint.  
  
### Adapters available with BizTalk Adapter Pack cannot be administered on a computer that only has BizTalk Server Administration component installed  
 If you have BizTalk Adapter Pack installed on a computer that only has the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console installed, the adapters installed as part of the BizTalk Adapter Pack are not available when you create a send port or receive location. This is because these adapters have a dependency on the BizTalk Runtime to be installed on the same computer.  
  
 Workaround – Install the BizTalk Server runtime on the computer that has the Adapter Pack and the BizTalk Server Administration component installed. You need not configure BizTalk Server on that computer.  
  
## Other Issues  
  
### Setup.bat for BizTalk Server Samples Runs with a 32-bit Command Prompt  
 For the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] samples shipped with this release, you must run the accompanying setup.bat files only from a 32-bit command prompt. Running the batch files from a 64-bit command prompt might result in a failure.  
  
### Run setup as Administrator  
 When installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], use the **Run as Administrator** option. Otherwise, the following errors may occur:  
  
 Internal Error 2761. Return Code: 1  
  
 MSI installation returned 1603 - Fatal error during installation.  
  
### Using certificates with 1024 key for encoding and signing results in failure of MIME-SMIME decoding  
 On Windows 8, when a message is encrypted and signed using certificates with 1024 key, MIME-SMIME decoding fails in authenticating the message. To avoid this issue, you can use certificates with 2048 key.  
  
### UDDI resolver with ESB Toolkit gives a Serialization error  
 While using UDDI with the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] you might encounter an XML serialization error when looking up the binding details. This error occurs if the binding key is not specified.  
  
### The itinerary designer for ESB Toolkit  
 The itinerary designer for the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] is now part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation media. You can find the itinerary designer at the root folder of the media and has the name `Microsoft.Practices.Services.Itinerary.DslPackage.vsix`. Earlier, this file was available at the location where you install the [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)], which typically is \Program Files\Microsoft [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].  
  
### EDI  
 EDI Batching is being used. When using an Arabic calendar or Arabic local settings, the orchestration suspends with the following error:  
  
 **Error Code: 0xC0C01B52 (Orchestration Engine Error)Error Description: Suspend due to persistence failure during dehydration.** Arabic Gregorian supports dates from *04/30/1900 00.00.00* to *05/13/2029 23:59:59*.  
  
 To resolve this behavior, enter a valid Arabic end date.  
  
### Enterprise Single Sign-On  
 When you install Enterprise Single Sign-On (ESSO) or when you restart the ESSO service you might see the following error logged in the Event Viewer.  
  
 **Failed to load \Program Files\Common Files\Enterprise Single Sign-On\SSOPSServer.dll Error code: 0x8007007E, The specified module could not be found.** You can safely ignore this error.