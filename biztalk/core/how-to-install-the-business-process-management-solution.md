---
title: "How to Install the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installing, examples"
  - "process management solution tutorial, installing"
  - "process management solution tutorial, deployment prerequisites"
ms.assetid: 930f3bb1-05e6-4b02-852d-6139aaf341f0
caps.latest.revision: 61
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Install the Business Process Management Solution
The following steps describe how to prepare the computer for installing the Business Process Management (BPM) solution, and how to install the solution on this computer.  
  
-   [Prepare the computer for installing the Business Process Management Solution](#step1)  
  
     In the preparation step, you create the folders, queues, and SQL database that will be used by the receive and send ports. You also create the two virtual directories for the client application, CSRWebApp, and the OrderBroker proxy Web Service.  
  
-   [Configure the computer for installing the Business Process Management Solution](#step3)  
  
-   [Install the Business Process Management Solution](#step5)  
  
> [!NOTE]
>  You will run some batch files to deploy the solution. We recommend that you redirect the output of the batch files to a text file to verify that the script completed successfully.  
  
##  <a name="step1"></a> Prepare the computer for installing the Business Process Management Solution  
  
#### To prepare the computer for installing the Business Process Management Solution  
  
1.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Services**. Using the **Services** console, make sure that the following services are running:  
  
    -   **FTP Publishing**  
  
    -   **Message Queuing**  
  
    -   **World Wide Web Publishing**  
  
2.  Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.  
  
3.  If you installed Windows SharePoint Services, exclude the (root) of the **Default Web Site** from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.  
  
    1.  Under **Virtual Server Configuration**, select **Configure virtual server settings**.  
  
    2.  On the **Virtual Server List** page, click **Default Web Site**.  
  
    3.  On the **Virtual Server Settings** page, click **Define managed paths**.  
  
    4.  In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.  
  
    5.  At a command prompt, perform an IISReset.  
  
##  <a name="step3"></a> Configure the computer for installing the Business Process Management Solution  
  
#### To configure the computer for installing the Business Process Management Solution  
  
1.  Log off the computer, and then log on to the computer as the BizTalk service account.  
  
2.  Open a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment variable to indicate the base folder for the E2E solutions. Then, exit the command prompt.  
  
    -   `setx BTSSolutionsPath "%ProgramFiles%\Microsoft BizTalk Server 2009\SDK\Scenarios"`  
  
        > [!NOTE]
        >  If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.  
  
        > [!NOTE]
        >  For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).  
  
3.  Open a command prompt, change the current directory to %BTSSolutionsPath%\BPM\HistoryDB folder, type `CreateDatabase.cmd`, and press ENTER to create the history database.  
  
    > [!NOTE]
    >  The user running the host specified as the handler for the SQL send adapter must have permissions to execute stored procedures on the SouthridgeVideoHistory database.  
  
4.  At a command prompt, run the following command to change the default script host to CScript.exe  
  
    -   `CScript /H:CScript`  
  
5.  At a command prompt, run the following command to create the CSRWebApp Web application  
  
    -   `iisvdir /create "Default Web Site" CSRWebApp "%BTSSolutionsPath%\BPM\CSRWebApp"`  
  
        > [!NOTE]
        >  For more information about iisvdir.vbs, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).  
  
6.  At a command prompt, run the following command to create a new IIS virtual directory for OrderBroker_Proxy.  
  
    -   `iisvdir /create "Default Web Site" BTSScn.BPM.OrderBroker_Proxy "%BTSSolutionsPath%\BPM\OrderBroker_Proxy"`  
  
    > [!NOTE]
    >  You can use Internet Information Services (IIS) Manager to create the Web Application. For more information about how to create applications in IIS 7.0, see the IIS 7.0 Documentation at [http://go.microsoft.com/fwlink/?LinkId=59263](http://go.microsoft.com/fwlink/?LinkId=59263).  
  
7.  Create a new IIS application pool and set its identity as a user that is a member of the BizTalk Isolated Host Users group and the IIS_WPG group, as follows:  
  
    1.  In Internet Information Services (IIS) Manager, right-click **Application Pools**, select **New**, and then select **Application Pool**.  
  
    2.  Type the **Application pool ID** (any value), and then click **OK**.  
  
    3.  Right-click the application pool that you created, and then select **Advanced Settings**.  
  
    4.  Expand **Process Model**, click in the right-column for the **Identity** setting, and then click **…**  
  
    5.  Select a user account (either a **Build-in account** or **Custom account** ) that has permissions to create and execute files in the Windows\Temp directory. When you configured BizTalk, the configuration process already set these permissions for the user it added to the BizTalk Isolated Host Users group. Specifying the same user is a good choice.  
  
8.  In Internet Information Services (IIS) Manager, expand **Web Sites**, expand **Default Web Site**, right-click **BTSScn.BPM.OrderBroker_Proxy**, point to **Manage Application**, and then click **Advanced Settings**.  
  
9. Set **Application Pool** to the application pool that you  created in the previous step.  
  
10. Repeat the previous two steps for the **CSRWebApp** application.  
  
11. Reset IIS to make sure all these changes take effect immediately. To do this, run **iisreset** at a command prompt.  
  
12. At a command prompt, change the current folder to the %BTSSolutionsPath%\BPM\Scripts, type `CreateQueues.vbs`, and then press ENTER to create the following private queues.  
  
    |Name|Transactional|Transaction protocol|  
    |----------|-------------------|--------------------------|  
    |ToFacilitiesQ|Yes|Native|  
    |FromFacilitiesQ|Yes|Native|  
    |FromFixedOrdersQ|Yes|Native|  
    |ToServicingSystemQ|Yes|Native|  
    |ToCSRSystemQ|No|HTTP|  
    |ToVendorSystemQ|No|HTTP|  
  
    > [!NOTE]
    >  You can use **Computer Management** snap-in to create the queues. For more information about how to create a private queue, see the Message Queuing documentation at [http://go.microsoft.com/fwlink/?LinkId=59264](http://go.microsoft.com/fwlink/?LinkId=59264). For more information about how to install MSMQ 3.0, see the Message Queuing documentation at [http://go.microsoft.com/fwlink/?LinkId=59265](http://go.microsoft.com/fwlink/?LinkId=59265).  
  
13. At a command prompt, change the current folder to the %BTSSolutionsPath%\BPM\Scripts, type `CreateTestDirectories.cmd`, and then press ENTER.  
  
    -   The following folders are crated in %SystemDrive%\BPMTest folder  
  
         CSRResponse-DSP  
  
         VendorResponse-DSP  
  
         OrderErrors-SP  
  
         ErrorResponse-RP-TestRL  
  
         Facilities-SP  
  
         Facilities-RP-TestRL  
  
         HistoryInsert-SP  
  
         HistoryUpdate-SP  
  
         Order-RP-TestRL  
  
         ServicingSystem-SP  
  
         Vendor-RP-TestRL  
  
         BizTalkErrors-SP  
  
    -   FromVendor folder is created in the %SystemDrive%\Inetpub\ftproot folder.  
  
        > [!NOTE]
        >  If the Windows system is not installed on the C drive, you should replace %SystemDrive% with C:. You have to match the folder names to the address in the binding files that the BPM solution provides.  
  
        > [!NOTE]
        >  The BizTalk service account must have read/write permission to the FromVendor folder.  
  
##  <a name="step5"></a> Install the Business Process Management Solution  
  
#### To install the Business Process Management Solution  
  
1. At a command prompt, change the current folder to %BTSSolutionsPath%\BPM, type `SetupBPM.bat`, and then press ENTER.  
  
   > [!NOTE]
   >  Before running SetupBPM.bat, in the files **%BTSInstallPath%/SDK/Scenarios/BPM/CSDWebApp/App_WebReferences/SouthridgeVideo_OrderBroker/OrderBrokerOrch_OrderPort.wsdl** and **%BTSInstallPath%/SDK/Scenarios/BPM/OrderBroker_Proxy/App_Code/OrderBrokerOrch_OrderPort.asmx.cs**, replace all instances of 8f8bbebbb3fb375a with XXXXXXXXXXXXXXXX.  
  
    The SetupBPM.bat performs the following tasks:  
  
   1.  Creates a unique strong name key (SNK) for signing the assemblies of the BPM Solution.  
  
   2.  Extracts the public key token from the SNK.  
  
   3.  Updates the binding files with the public token.  
  
   4.  Builds the BPM solution, and installs OpsAdapter.  
  
   5.  Builds the SSOApplicationConfig in the %BTSSolutionsPath%\Common folder.  
  
2. Deploy the Southridge Video business rules using the Business Rule Engine Deployment Wizard:  
  
   1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rules Engine Deployment Wizard**.  
  
      > [!NOTE]
      >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
   2. On the **Welcome** page, click **Next**.  
  
   3. On the **Deployment Task** page, select **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.  
  
   4. On the **Policy Store** page, keep all other default settings, and then click **Next**.  
  
   5. On the **Import Rules Engine Policy/Vocabulary file** page, click **Browse**, select the DecodeAndValidateOrderRules.xml file in the %BTSSolutionsPath%\BPM\Rules folder, and then click **Next**.  
  
   6. On the **Ready** page, click **Next**, and then on the **Importing Policy/Vocabulary** page, click **Next**  
  
   7. On the Completion page, select **Run the wizard again** to open the Wizard again, and then click **Finish**.  
  
   8. On the **Welcome** page, click **Next**.  
  
   9. On the **Deployment Task** page, select **DeployPolicy**, and then click **Next**.  
  
   10. On the **Policy Store** page, keep all other default settings, and then click **Next**.  
  
   11. On the **Deploy Policy** page, select **DecodeAndValidateOrder 1.0** in the **Rule Engine Policy** drop-down list, and then click **Next**.  
  
   12. On the **Ready** page, click **Next**, and then on the **Deploying Policy** page, click **Next**.  
  
   13. On the Completion page, click **Finish**.  
  
3. If you install the BPM solution on a 64-bit computer, then  
  
   1.  Open a 32-bit command prompt as follow: Click **Start**, click **Run**, type `%SYSTEMROOT%\SYSWOW64\CMD.EXE`, and then press ENTER.  
  
   2.  At the 32-bit command prompt, change the directory to the %BTSSolutionsPath%\BPM\Scripts folder.  
  
   3.  Using Notepad, open the CreateSouthridgeVideoApplication.cmd, and then replace "%CommonProgramFiles%\Enterprise Single Sign-On\ssomanage.exe" with "%SystemDrive%\Program Files\Common Files\Enterprise Single Sign-On\ssomanage.exe".  
  
       > [!NOTE]
       >  At a 32-bit command prompt, the %CommonProgramFiles% variable is changed to "%ProgramFiles(x86)%\Common Files". Because the SSO administrative utility is installed in the %ProgramFiles% even on a 64-bit computer, you must fix the path. The DeployBPM.cmd calls CreateSouthridgeVideoApplication.cmd.  
  
   4.  At the 32-bit command prompt, type type `DeployBPM.cmd`, and then press ENTER.  
  
       > [!NOTE]
       >  The DeployBPM.cmd must be run at a 32-bit command prompt because it includes the VB Script accessing x86 objects that requires the x86 version of cscript.exe.  
  
4. At a command prompt, change the current folder to %BTSSolutionsPath%\BPM\Scripts, type `DeployBPM.cmd`, and then press ENTER. The DeployBPM.cmd performs the following tasks:  
  
   1.  Creates BizTalk Applications for the BPM Solution.  
  
   2.  Adds references between the applications.  
  
   3.  Imports the binding files.  
  
   4.  Deploys the BAM definition files.  
  
   5.  Registers the SouthridgeVideo event source.  
  
   6.  Creates a Single Sign-On (SSO) affiliated application, and saves configuration values to the SSO application.  
  
5. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
   1.  In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Applications**, expand **BTSScn.BPM.OrderBrokerApp**, expand **Receive Locations**, right-click **Vendor-RP-RL**, and then click Properties.  
  
   2.  On the **Properties** dialog box, click **Configure**, and then enter values as the following table on the **Transport Properties** dialog box:  
  
       |Property Name|Value|  
       |-------------------|-----------|  
       |**Server**|`localhost`|  
       |**User Name**|\<*BizTalk service account name*\>|  
       |**Password**|\<*BizTalk service account password*\>|  
  
6. Run the BPM Solution. For more information about running the solution, see [How to Run the Business Process Management Solution](../core/how-to-run-the-business-process-management-solution.md).  
  
## Next Steps  
 You test how the Business Management Solution works in [How to Run the Business Process Management Solution](../core/how-to-run-the-business-process-management-solution.md).  
  
## See Also  
 [Before Installing the Business Process Management Solution](../core/before-installing-the-business-process-management-solution.md)   
 [Developer Machine Setup for the Business Process Management Solution](../core/developer-machine-setup-for-the-business-process-management-solution.md)