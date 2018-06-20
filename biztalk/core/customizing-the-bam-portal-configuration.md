---
title: "Customizing the BAM Portal Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 507bd5f0-b2a0-4d52-85f8-9d984138ca79
caps.latest.revision: 47
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Customizing the BAM Portal Configuration
There are a number of configurable options on the BAM portal. The following procedures show you how to modify the BAM portal to obtain the best user experience.  

> [!NOTE]
>  When configuring the portal as a non-administrator impersonated user, it may be necessary for you to log off and then log back on before you have access to the BAM portal features without being asked to enter your credentials. For example, consider the following scenario:  
>   
>  You configure the Web service or BAM portal with a non-administrator impersonated user. You then set permissions on the portal such that the Everyone group does not have access to the portal. You then create a local group called PortalUsersGroup and assign that group as the Portal Users group. This means that only users in that group have access to the portal. After you have configured the BAM portal, add the current user to the Portal Users group. When you open the BAM portal, you will be asked for your credentials. If you log off and log back on, however, you are able to open the BAM portal without being asked for your credentials.  
>   
>  BizTalk Server supports local group and user accounts only in single computer configurations. BizTalk Server supports domain group and user accounts in both single and multiple computer configurations.  

## Running the BAM Portal in a 64-bit Environment  
 If you are using Internet Information Services (IIS) in a 64-bit environment, you must set IIS to 32-bit mode to run the BAM portal. 

> [!IMPORTANT]
>  You do not have to set IIS7 to 32-bit mode.  

#### To set a 64-bit mode IIS installation to 32-bit mode  

1.  Open a command prompt and run the **adsutil** command. To do this, click **Start**, click **Run**, and then type **cmd**.  

2.  Type the following at the command prompt: `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`.  

3.  Close the command prompt.  

## Configuring the BAM Portal Banner  
 You can modify the BAM portal page to display similar text and graphics about your business:  

- The Windows Server System logo, which is located in the upper-right corner of the BAM portal page.  

  In the following procedure you edit a cascading style sheet file (.css file) to customize the look of the BAM portal. Modifications to the specified classes are the only modifications supported. As much as possible, the impact of modifications to classes has been isolated so that errors made during the modification process leave the BAM portal in a working state.  

> [!CAUTION]
>  Modifying other classes in the styles.css file will hide data and portal features, and may make the portal unusable.  

#### To configure the banner  

1. Edit the BAM portal web.config file. To do this, click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then click **OK**.  

2. The main page quick-start contents are replaceable by modifying the following line: \<add key="MainPageContentUrl" value="~/MainPageContent.htm"/\>. Change **MainPageContent.htm** in the value field to point to your own HTML file. The HTML file must be in the same directory as the web.config file.  

3. Change the page identifying text by adding the following line to the web.config file: \<add key=”PortalTitle” value=”New Identifying text”/\>. Change the value field to contain the text to identify the portal.  

4. Edit the BAM portal styles.css file. Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\Styles.css, and then click **OK**.  

5. Change the logo in the upper-right corner by locating the .headerLogo div class and changing the following line:   background-image: url("../images/WSS_Logo.gif"); to point to the image file you have created. We recommend that you use a .gif format image.  

6. Change the SharePoint icon by locating the .headerPageIcon div class and changing the following line: background-image: url("../images/btsSuiteProduction.gif"); to point to the image file you have created.  

7. Save the file.  

8. Open the BAM portal to view your changes.  

## Modifying the BAM Portal web.config File  
 If your BAM portal resides on a server that uses Enterprise Single Sign-On (SSO) certificates for Secure Sockets Layer (SSL), you must configure the portal to accept the proper URL for the certificate.  

#### To modify the BAM portal to support SSL sites  

1. Open the web.config file using Notepad. Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then click **OK**.  

2. Modify the following two lines in the file to point to the location of your SSL-enabled portal:  

   ```  
   <add key="BamQueryWSUrl" value="http://localhost/BAM/BamQueryService/BamQueryService.asmx"/>  
   <add key="BamManagementWSUrl" value="http://localhost/BAM/BamManagementService/BamManagementService.asmx"/>  
   ```  

3. Save the file.  

   The BAM portal displays and accepts data formatted according to the culture for which it has been configured. The configuration is specified in the web.config file. The Web portal ignores the “Accept Language” information sent by Internet Explorer. For example, suppose that you are running Internet Explorer which is set for a Japanese culture setting and have configured the BAM portal to use the U.S. English culture setting. In this case data items, such as dates and integers, will be displayed, accepted, and sorted using rules appropriate to the U.S. English culture setting rather than rules appropriate to the Japanese culture setting. Any culture-specific information entered using Japanese formatting will be considered invalid by the BAM portal because it will expect data formatted for U.S. English.  

   To obtain consistent handling of display and formatting of data that is variable based on the culture settings, choose a language that is appropriate for all BAM portal clients. Configure the BAM portal for this culture. You must ensure that every client is set to the chosen culture by installing the Multilingual User Interface Pack.  

   For non-U.S. English installations of BAM it may be necessary to set the culture parameter in the web.config file. Cases where you may need to do this are:  

-   To localize the format of date and time displays.  

-   To localize the format of currency displays.  

#### To modify the culture setting of the portal  

1. Open the web.config file using Notepad. Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then click **OK**.  

2. Modify the culture attributes in the following line in the file to reflect the appropriate globalization settings:  

   ```  
   <globalization requestEncoding="utf-8" responseEncoding="utf-8" culture="de-DE" uiCulture="en" />  
   ```  

3. Save the file.  

   In cases where you are experiencing time-outs while waiting for large SQL queries, it may be necessary to increase the query service time-out value.  

#### To increase the query service time-out value  

1. Open the web.config file using Notepad. Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config, and then click **OK**.  

2. The default value for the QueryServiceTimeout is 45 seconds. Modify the value in the following line to increase or decrease the time-out interval:  

   ```  
   <add key="QueryServiceTimeout" value="45" />  
   ```  

3. Save the file.  

   In a multiserver environment there may be times when a server is offline. When this happens, users of the portal may experience time delays where the BAM portal stops responding. To improve the user experience you can modify the server retry interval. This creates a minimum time during which the BAM query Web service assumes that the server is offline after a connection has failed once.  

   The value indicates that if a local database times out while trying to contact a remote database, the data is marked as incomplete and the local computer will not attempt to connect to the remote database until the specified time has elapsed.  

#### To increase the retry interval for distributed activities in a multiserver environment  

1. Open the web.config file using Notepad. Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\BAMManagementService\web.config, and then click **OK**.  

2. The default value for the ServerRetryInterval is five minutes. Modify the value in the following line to increase or decrease the server retry interval:  

   ```  
   <add key="ServerRetryInterval" value="5"/>  
   ```  

3. Save the file.  

#### To configure how alert notification options are presented in the BAM portal  

1. Open the web.config file using Notepad. Click **Start**, click **Run**, type notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config, and then click **OK**.  

2. Modify the value field in the \<add key="AlertNotificationOptions" value="" /\> line of the web.config file with a comma-delimited list specifying valid notification options with one of the following values. An empty value displays all notification options available on the server in the order returned by the server. Any unrecognized value is equivalent to an empty value.  


   |    Value    |                                              Description                                               |
   |-------------|--------------------------------------------------------------------------------------------------------|
   | File, Email | File and E-mail options are displayed. In the drop-down list, File is displayed first and then E-mail. |
   | Email, File | File and E-mail options are displayed. In the drop-down list, E-mail is displayed first and then File. |
   |    File     |                             Only File notification is displayed in portal.                             |
   |    Email    |                            Only E-mail notification is displayed in portal.                            |


3. Save the file.  

## Distributed Server Environments  
 If your installation of the BAM portal places the alerts and the BAM portal on different servers, you will see the following error in the event log: "System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> The registry entries for the specified instance of Notification Services could not be found."  

#### To configure the portal and alerts on different servers  

1. Open a command prompt.  

2. Run **C:\Program Files\Microsoft SQL Server\90\Notification Services\9.0.242\Bin\nscontrol register -name bamalerts -server**<em>\<server name\></em> Replace *\<server name\>* with the name of the server.  

3. Press F5 to refresh your browser.  

## Configuring IIS to Allow the BAM Portal to Use the Kerberos Network Protocol  
 If you want to use the Kerberos network protocol with the BAM portal you must modify the ACL security for the Web portal. If IIS is not configured properly, users will receive the following error:  

 HTTP Error 401.1 - Unauthorized: Access is denied due to invalid credentials.  

 For additional information about modifying the IIS security settings, see the Knowledge Base article at [http://go.microsoft.com/fwlink/?LinkId=57922](http://go.microsoft.com/fwlink/?LinkId=57922).  

## Viewing Aggregate BAM Data in the BAM Portal in SQL Server 2008  Deployments  
 To view aggregate data in the BAM portal from a client computer connecting to the BAM portal when the deployment environment uses SQL Server 2008, you must install Microsoft SQL Server 2008 Analysis Services 10.0 OLE DB Provider on the client computer. If the analysis services are not installed users will receive the following error message:  

 The server *\<servername\>* cannot be contacted or is too busy.  



## See Also  
 [Planning for the BAM Portal](../core/planning-for-the-bam-portal.md)