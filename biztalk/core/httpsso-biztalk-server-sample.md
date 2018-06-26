---
title: "HTTPSSO (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP adapters, examples"
  - "SSO, examples"
  - "SSO, HTTP adapters"
  - "examples, HTTP adapters"
  - "HTTP adapters, SSO"
  - "examples, SSO"
ms.assetid: 322360df-81d2-4a73-9512-bda9382351a2
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTPSSO (BizTalk Server Sample)
The HTTPSSO sample demonstrates how to use the Enterprise Single Sign-On (SSO) feature with the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP adapter.  

> [!NOTE]
>  This sample is not supported on 64-bit operating systems.  

## What This Sample Does  
 This sample demonstrates an end-to-end scenario that uses SSO and the BizTalk HTTP Send and Receive adapters to simulate how SSO allows a user to avoid supplying additional credentials to log on to non-Microsoft Windows systems after Windows authenticates them.  

 The sample also uses the administration and mapping modules of SSO to create affiliate application and SSO mappings using the interop client DLL of SSO.  

 The sample demonstrates the use of SSO by implementing the following aspects of an end-to-end scenario:  

- User interface, represented by a Microsoft Internet Information Services (IIS) virtual directory configured to use Windows integrated authentication.  

- Back-end system, represented by an IIS virtual directory configured to use basic authentication.  

- Back-end database, represented by the SQL sample database Northwind.  

  This sample assumes that you have installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SSO. You must have administrator privileges for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], IIS, SSO, and COM+ on Windows XP Professional. You must also be a member of SSO Administrators, BizTalk Server Administrators, and BizTalk Isolated Host Users Windows groups.  

  Effective use of this sample assumes that you have sufficient knowledge of SSO and the BizTalk HTTP adapter. For example, you should know what an affiliate application is in the context of SSO. For information about these topics, see [Using SSO](../core/using-sso.md). Also see [HTTP Adapter](../core/http-adapter.md).  

  After you complete the configuration, this sample works as follows:  

1. When you click **Finish** in the wizard application that comprises the user interface for this sample, an instance of Internet Explorer starts and passes the URL of the BizTalk HTTP Receive DLL.  

2. BizTalk Server, with the help of SSO, effectively forwards the HTTP request to the file EmployeeData.aspx in an IIS virtual directory that has been configured with basic authentication. This ASPX file simulates the entry point into a non-Windows back-end system. Because you are using SSO, the HTTP request includes the configured credentials that simulate a logon account to the simulated back-end system.  

3. The ASPX file accesses a modified version of the SQL sample database Northwind to retrieve employee data corresponding to the simulated back-end system credentials.  

4. The ASPX file returns the retrieved employee data in an HTTP response.  

5. BizTalk Server routes the HTTP response to Internet Explorer, which displays the returned employee data to the user.  

   If you bypass BizTalk Server and SSO, and browse directly to the file EmployeeData.aspx, a Windows dialog box will prompt you for your credentials.  

   For a sample that shows how to use the command-line utility ssomanage.exe to configure SSO, such as creating affiliate applications and user mappings, see [Manage (BizTalk Server Sample)](../core/manage-biztalk-server-sample.md).  

## Where to Find This Sample  
 \<*Samples Path*\>\SSO\HTTPSSO\  

 The following table shows the files in this sample and describes their purpose.  

|File(s)|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs, SsoSample.csproj|Project and related files for this HTTP SSO sample.|  
|SsoSample.cs|Top-level Microsoft Visual C# source file for the HTTP SSO graphical application that constitutes much of this sample. This file contains the SSO configuration code, in a class named **SsoConfigurator** that is ultimately the point of this sample.|  
|In the \Scripts folder:<br /><br /> EmployeeData.aspx|Used to access and query the back-end database (in this case, the SQL Northwind database) when an employee initiates a request to view personal data, either directly or by using SSO.|  
|In the \Scripts folder:<br /><br /> ValidateUser.aspx|Simple test to validate a user and report if that user was validated, either directly or by using SSO.|  
|In the \UI folder:<br /><br /> AddApplication.cs, AddApplication.resx, AddMapping.cs, AddMapping.resx, App.ico, BtsPage.cs, BtsPage.resx, ExecutePage.cs, ExecutePage.resx, FinishPage.cs, FinishPage.resx, IisPage.cs, IisPage.resx, InfoPage.cs, InfoPage.resx, PageBase.cs, PageBase.resx, SsoPage.cs, SsoPage.resx, SsoSampleWizard.cs, SsoSampleWizard.resx, WelcomePage.cs, WelcomePage.resx, WorkPage.cs, WorkPage.resx|Auxiliary Visual C# source files, and their associated XML-formatted resource files, for the HTTP SSO graphical application that constitutes much of this sample.|  

## Building and Initializing This Sample  

#### To build and initialize the HTTPSSO sample  

1. Create a local Windows account that Microsoft Internet Information Services (IIS) can use for basic authentication. SSO maps the Windows domain account to this local Windows account. For example, use your last name to create a local Windows account.  

   > [!NOTE]
   >  If you are running on a domain controller, you can create domain accounts and map your logged on domain account to this account.  

2. Using Microsoft SQL Server Enterprise Manager, open the **Employees** table in the Northwind sample database, and then add a row corresponding to the local Windows account that you just created, including sample data for the various columns. The value you add to the LastName column in the Employees table must be the same as the user name of the local Windows account you added in step 1.  

3. Ensure the ASP.NET account (ASPNET) has read privileges to the Northwind database.  

4. Open the project file SsoSample.csproj using Visual Studio.  

5. On the **Build** menu, click **Build Solution**.  

   > [!NOTE]
   >  You may be asked to save a solution file before the build can proceed.  

    If you cannot find the following BizTalk assembly references for the project, delete them, re-add them from the indicated locations, and build again:  

   - **Microsoft.BizTalk.ExplorerOM**. By default, the Microsoft.BizTalk.ExplorerOM.dll file is located in the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Developer Tools\\.  

   - **Microsoft.BizTalk.SSOClient.Interop**. By default, the Microsoft.BizTalk.Interop.SSOClient.dll file is located in the folder \<*ProgramFiles*\>\Common Files\Enterprise Single Sign-On\\.  

     This produces the executable file SsoSample.exe in the following folder:  

     \<*Samples Path*\>\SSO\HTTPSSO\bin\Debug\  

## Running This Sample  

> [!NOTE]
>  If you run this sample on IIS 6.0 in Worker Process Isolation Mode, application pools are created for both virtual directories. You must manually configure identity for these two application pools in your Windows account (you can configure identity in Internet Information Services Manager).  

#### To run the HTTPSSO sample  

1. Run the executable file SsoSample.exe, found in the following folder:  

    \<*Samples Path*\>\SSO\HTTPSSO\bin\Debug\  

    The wizard application for this sample opens.  

2. On the Welcome page, accept the default setting for configuring IIS, SSO, and BizTalk, and then click **Next**.  

3. On the IIS Configuration page, accept the default settings for the two IIS virtual directories you want to create, and then click **Next**.  

4. On the SSO Configuration page, accept the default settings for the affiliate application, which is accessible using the **Add application** button.  

5. On the SSO Configuration page, accept most of the default settings for the user mappings, accessible using the **Add mapping** button. Provide values for the following two settings based on the local Windows account you added when building and initializing this sample.  


   |        Setting         |                         Value                         |
   |------------------------|-------------------------------------------------------|
   |   External user name   |   Set to the added local Windows user account name.   |
   | External user password | Set to the added local Windows user account password. |


6. On the SSO Configuration page, click **Next**.  

7. On the BizTalk Configuration page, accept the default settings for the send and receive ports, and so on, and then click **Next**.  

   > [!NOTE]
   >  You can change the default send port setting from **EmployeeData.aspx** to **ValidateUser.aspx** if you want to see simple user validation rather than sample data pulled from the Employee table of the Northwinds SQL database. Making this change changes the nature of the output displayed in the browser after clicking **Finish** in step 9.  

8. Review the status messages corresponding to the IIS, SSO, and BizTalk configuration being performed. You can find the code that is run during this phase in the **IisConfigurator**, **SsoConfigurator**, and **BtsConfigurator** classes defined in the file SsoSample.cs. After configuration has completed, click **Next**.  

9. On the final page of the wizard application, accept the default settings for **Start browser at** (a selected check box and a text box with the URL http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll?<message/>), and then click **Finish**.  

     An instance of Internet Explorer will open, and soon display the sample employee data that you added to the Employee table of the Northwinds SQL database.  

   For comparison purposes, you can bypass BizTalk and SSO and browse directly to either of the ASPX files:  

- http://localhost/SsoSampleServerApplication/ValidateUser.aspx  

- http://localhost/SsoSampleServerApplication/EmployeeData.aspx  

  In both cases, because you bypass BizTalk and SSO, you are prompted for your authentication information by IIS (use the local Windows account information you created previously).  

## Comments  
 The SsoSample.exe wizard application configures two IIS virtual directories:  

- The first virtual directory is configured with Windows integrated authentication and corresponds to the BizTalk HTTP Receive ISAPI extension. It must be associated with the .dll file BTSHTTPReceive.dll located in the following folder:  

   \<*Install Path*\>\HttpReceive  

- The second virtual directory is configured with basic authentication and simulates a back-end system that accepts a user ID and password to authenticate the user. It must be associated with one or the other of the ASPX files, ValidateUser.aspx or EmployeeData.aspx, located in the following folder:  

   \<*Samples Path*\>\SSO\HTTPSSO\Scripts  

  You can use the SsoSample.exe wizard application to configure one or more affiliate applications. For each of these affiliate applications, you can create one or more user mappings. Each of these user mappings maps a Windows user account to an account that you use to access a specific back-end system. In this sample, that account is a local Windows account that you use to authenticate with the second IIS virtual directory that is simulating a genuine back-end system.  

  To rerun this sample, you have several choices:  

- Browse directly to the following URL in Internet Explorer:  

   http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll?<message/>  

- Run the wizard application again, but clear all of the configuration check boxes on the first page.  

- Run the wizard application again, leave the configuration check boxes selected in the first page, but carefully and appropriately configure additional BizTalk items, affiliate applications, and so on, so that configuration errors do not occur.  

  To clean up from this sample, use the following procedure.  

#### To clean up from this sample  

1.  As appropriate, reverse the manual configuration that you performed, such as removing the local Windows account.  

2.  Remove IIS applications that correspond to the virtual directories, and then delete the IIS virtual directories created by this sample.  

3.  Using BizTalk Administration console, unenlist and then delete the send port associated with this sample. Then delete the receive port (and its receive location) associated with this sample.  

4.  Use the Ssomanage application (located in \Program Files\Common Files\Enterprise Single Sign-On\\) to delete the SSO application for this sample:  

    ```  
    Ssomanage –deleteapp SsoSampleApplication  
    ```  

## See Also  
 [SSO (BizTalk Server Samples Folder)](../core/sso-biztalk-server-samples-folder.md)