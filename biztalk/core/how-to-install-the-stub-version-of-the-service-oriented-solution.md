---
title: "How to Install the Stub Version of the Service Oriented Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IIS, installing virtual directories [service solutions]"
  - "service solution tutorial, IIS virtual directories"
  - "service solution tutorial, stub version"
  - "deploying, BAM solutions [service solutions]"
  - "service solution tutorial, solutions [BAM]"
  - "service solution tutorial, service solutions"
  - "SSO, configuring"
  - "IBM WebSphere MQ Client"
  - "service solution tutorial, IBM WebSphere MQ Client"
  - "installing, tutorials"
  - "service solutions, deploying"
  - "service solution tutorial, SSO"
  - "BAM, deploying solutions"
  - "service solution tutorial, building solutions"
  - "service solution tutorial, installing"
ms.assetid: 45de7681-4df0-47a4-a02c-509140423a1e
caps.latest.revision: 53
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Install the Stub Version of the Service Oriented Solution
The following steps describe how to prepare your computer before you install the stub version of the service oriented solution, and then how to install the solution on your computer.  
  
-   [Prepare the computer for installing the stub version of the Service Oriented Solution](#step1)  
  
-   [Install the IBM WebSphere MQ Client for Windows](#step3)  
  
-   [Create the virtual directories in IIS for the Service Oriented Solution](#step5)  
  
-   [Build the Service Oriented Solution](#step7)  
  
-   [Create the Enterprise Single Sign-On (SSO) entries and values in the SSO database](#step9)  
  
-   [Deploy the BAM definition for the Service Oriented Solution](#step11)  
  
-   [Deploy the Service Oriented Solution](#step13)  
  
##  <a name="step1"></a> Prepare the computer for installing the stub version of the Service Oriented Solution  
  
#### To prepare the computer for installing the stub version of the Service Oriented Solution  
  
1. Make sure that the **Default Web Site** is configured to use ASP.NET 2.X.  
  
   1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
   2.  In the **Internet Information Services (IIS) Manager**, the machine name, expand  **Sites**, expand **Default Web Site**, expand **aspnet_client**, expand **system_web**.  
  
   3.  Make sure that the sub-folder is 2.X.  
  
2. Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Services**. Using the **Services** console, make sure that the following services are running:  
  
   -   **World Wide Web Publishing**  
  
3. Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.  
  
4. If you installed Windows SharePoint Services, exclude the (root) of the **Default Web Site** from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.  
  
   1.  Under **Virtual Server Configuration**, select **Configure virtual server settings**.  
  
   2.  On the **Virtual Server List** page, click **Default Web Site**.  
  
   3.  On the **Virtual Server Settings** page, click **Define managed paths**.  
  
   4.  In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.  
  
   5.  At a command prompt, perform an IISReset.  
  
5. Log off the computer, and then log on to the computer as the BizTalk service account.  
  
6. Open a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment. Then, exit the command prompt.  
  
   - setx BTSSolutionsPath "[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"  
  
     > [!NOTE]
     >  If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.  
  
     > [!NOTE]
     >  For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).  
  
##  <a name="step3"></a> Install the IBM WebSphere MQ Client for Windows  
  
#### To install the IBM WebSphere MQ Client for Windows  
  
1. Download the latest version of IBM WebSphere MQ Client for Windows.  
  
   > [!NOTE]
   >  Even if the stub version of the solution doesn't require IBM WebSphere Server, the client application references the amqmdnet.dll file provided by IBM WebSphere MQ Client for Windows, so you must install it. The client of the stub version does not actually call an API in the DLL. It is required only for compiling and running the client application. You can download IBM WebSphere MQ Client for Windows from the IBM Web site.  
  
2. Install IBM WebSphere MQ Client for Windows.  
  
   > [!NOTE]
   >  You don't need to configure IBM WebSphere MQ Client for Windows. Keep all of the default settings.  
  
3. Add WebSphere MQ classes for the .NET assembly to the global assembly cache (GAC).  
  
   1. At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, navigate to the directory \<IBM MQSeries Installation Directory\>\bin.  
  
   2. Run the following command (make sure gacutil.exe is in the path environment):  
  
       `gacutil.exe /i amqmdnet.dll`  
  
##  <a name="step5"></a> Create the virtual directories in IIS for the Service Oriented Solution  
  
#### To create the virtual directories in IIS for the Service Oriented Solution  
  
1.  In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **Add Application Pool**.  
  
     On the **Add Application Pool** dialog box, type `SSOStubAppPool` in the **Name** text box, and then click **OK**.  
  
     The virtual directories that service-oriented solution uses include the published Web service for the stub version of orchestrations, the stub SAP Web service, the stub Payment Tracker Web service, and the stub Pending Transaction Web service.  
  
2.  In the **Internet Information Services (IIS) Manager**, right-click the application pool that you just created, and then click **Advanced Settings**.  
  
3.  Click in the column to the right of the **Identity** property, and then click the ellipsis (**…**) button.  
  
4.  In the **Application Pool Identity** dialog box, select the **Custom Account** option, and then click **Set**.  
  
5.  In the **Set Credentials** dialog box, specify a username and password, confirm the password, and then click **OK**.  
  
    > [!NOTE]
    >  This user must have permission to execute the Orchestration Proxy Web service, and must be added to one of the BizTalk Server Administrators, SSO Administrators, or SSO Affiliated Administrators groups  
  
6.  Click **OK** to close the **Application Pool Identity** dialog box.  
  
7.  Click **OK** to close the **Advanced Settings** dialog box.  
  
8.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.  
  
    1.  Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub  
  
         PATH = \<BizTalk Install Directory\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Stub  
  
         Access Permissions = Read, Run scripts  
  
    2.  Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP  
  
         PATH = \<BizTalk Install Directory\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP  
  
         Access Permissions = Read, Run scripts  
  
    3.  Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions  
  
         PATH = \<BizTalk Install Directory\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans  
  
         Access Permissions = Read, Run scripts  
  
    4.  Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker  
  
         PATH = \<BizTalk Install Directory\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PaymentTrack  
  
         Access Permissions = Read, Run scripts  
  
9. In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub, click **Properties**, and then modify the settings as follows:  
  
    1.  On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.  
  
    2.  Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes. Click **OK** to exit.  
  
10. In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, click **Properties**, and then modify the settings as follows:  
  
    1.  On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.  
  
    2.  Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable Anonymous Access**. Click **OK** to exit.  
  
11. In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows:  
  
    1.  On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.  
  
    2.  Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable Anonymous Access**. Click **OK** to exit.  
  
12. In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker, click **Properties**, and then modify the settings as follows:  
  
    1.  On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.  
  
    2.  Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable Anonymous Access**. Click **OK** to exit.  
  
##  <a name="step7"></a> Build the Service Oriented Solution  
  
#### To build the Service Oriented Solution  
  
1. Start **Visual Studio Command Prompt**.  
  
   > [!NOTE]
   >  In the files **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Inline\app_code\customerserviceport.asmx.cs** and **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Stub\app_code\customerserviceport.asmx.cs**, replace all the instances of 17f20caea2afcc8c with a1054514fc67bded.  
  
2. At the Visual Studio Command Prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln folder, and then run the following command to build the stub version of service-oriented solution.  
  
   -   `SetupBTSSoln.bat`  
  
   > [!NOTE]
   >  In the files listed below, replace all the instances of 17f20caea2afcc8c with the current public key token.  
   > 
   > - %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_CustomerServiceResponse.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_ErrorResponse.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CreditLimitResponse.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CustomerServiceResponseDenied.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_LastPaymentResponseTimeout.btm.cs  
   >   -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_PendingTransactionResponse.btm.cs  
  
##  <a name="step9"></a> Create the Enterprise Single Sign-On (SSO) entries and values in the SSO database  
  
#### To create the Enterprise Single Sign-On (SSO) entries and values in the SSO database  
  
1.  Open a command prompt, change the current directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts, and then run the following command to set the PATH environment for the Enterprise Single Sign-On folder.  
  
    -   `Set PATH=%PATH%;%ProgramFiles%\"Common Files\Enterprise Single Sign-On"`  
  
2.  At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, open ConfigStoreApp.xml using Notepad, and then review the contents of the file.  
  
    > [!NOTE]
    >  This file defines the configuration store application in SSO that the scenario uses to store configuration parameters. Some of the configuration parameters include the **Timeout** value used to communicate with SAP (for all three versions). No changes to this file are necessary.  
  
3.  At the command prompt, run the following command to create the SSO configuration store application.  
  
    -   `ssomanage -createapps ConfigStoreApp.xml`  
  
4.  At the command prompt, open SetConfigValuesInSSO.cmd using Notepad, and then review the contents of the file  
  
    > [!NOTE]
    >  This command file sets the values of the configuration parameters in the SSO database. It contains several set statements that set the values in local variables in the beginning of the command file. The **SAPAdapterTimeout**, **PendingTransactionsAdapterTimeout**, and **PaymentTrackingAdapterTimeout** values are used in the stub and adapter version. The remaining values are used in the inline version. No changes to this file are necessary for stub version.  
  
5.  At the command prompt, type `SetConfigValuesInSSO.cmd`, and then press ENTER to store the values in the SSO configuration store application.  
  
6.  At the command prompt, run the following command to enable tickets in SSO:  
  
    -   `ssomanage -tickets yes yes`  
  
##  <a name="step11"></a> Deploy the BAM definition for the Service Oriented Solution  
  
#### To deploy the BAM definition for the Service Oriented Solution  
  
1.  At a command prompt, type the following command, and then press ENTER. This sets the path to find the BAM utility:  
  
    -   SET PATH=%PATH%;%programfiles%\Microsoft BizTalk Server\Tracking  
  
2.  At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\BAM folder, and type the following command, and then press ENTER:  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
        > [!NOTE]
        >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
##  <a name="step13"></a> Deploy the Service Oriented Solution  
  
#### To deploy the Service Oriented Solution  
  
1.  Open a command prompt and change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.  
  
2.  Modify the **DeployStubBinding.cmd** file by replacing all the instances of “debug” and “development” with “release”.  
  
3.  Open a command prompt and change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder. Type the following command, and then press ENTER:  
  
    -   `DeployStubBinding.cmd`  
  
4.  At the command prompt, run the following command to start the orchestrations for the stub version  
  
    -   `Startstub.vbs`  
  
## Next Steps  
 You test how the stub version of the service-oriented solution works in [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).  
  
## See Also  
 [Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md)   
 [How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)   
 [Developer Machine Setup for the Service Oriented Solution](../core/developer-machine-setup-for-the-service-oriented-solution.md)