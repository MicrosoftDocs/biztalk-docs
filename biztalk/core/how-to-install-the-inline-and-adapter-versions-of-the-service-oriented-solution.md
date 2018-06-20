---
title: "Install the Inline and Adapter Versions of the Service Oriented Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6050cfe9-4e94-4a55-8b24-fbcc74d9e8f4
caps.latest.revision: 97
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Install the Inline and Adapter Versions of the Service Oriented Solution
The following steps describe how to prepare the computer for installing the inline and adapter versions of the service oriented solution, and how to install the solution on this computer.  

> [!NOTE]
>  - The service oriented solution is located in the folder \<*BizTalk Server Installation Folder*\>\SDK\Scenarios\SO.  
>  - If you don’t have a mainframe for the solution, you can modify the port binding to use the stub Web service for Pending Transactions. The Web service generates transactions locally to emulate the mainframe transactions.  

##  <a name="step1"></a> Prepare the computer for installing the adapter and inline versions of the Service Oriented Solution  

1. If you installed Windows SharePoint Services, exclude the (root) of the Default Web Site from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.  

   1.  Under **Virtual Server Configuration**, select **Configure virtual server settings**.  

   2.  On the **Virtual Server List** page, click **Default Web Site**.  

   3.  On the **Virtual Server Settings** page, click **Define managed paths**.  

   4.  In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.  

   5.  At a command prompt, perform an IISReset.  

2. Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.  

3. Log off the computer, and then log on to the computer as the BizTalk service account.  

4. At a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment variable. Then, exit the command prompt.  

   - setx BTSSolutionsPath [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"  

     > [!NOTE]
     >  If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.  

     > [!NOTE]
     >  For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).  

##  <a name="step3"></a> Remove the stub version of the Service Oriented Solution  

1. Open the **BizTalk Server Administration Console** as follows: Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  

2. In the **BizTalk Server Administration Console**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, right-click **BTSScn.SO.CustomerService**, and then click **Stop**. In the **Stop Application** dialog box, select **Full Stop - Terminate Instances**, and then click **Stop**.  

   > [!NOTE]
   >  You don't need to remove the stub version for installing the inline and adapter versions. If you want to put all the versions together, you should skip this step.  

3. Open a command prompt, type the following command, and then press ENTER. This command changes the default script host to CScript.exe:  

   -   `cscript /H:CScript`  

4. At the command prompt, change the current directory to %BTSSolutonsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER:  

   -   `UnEnlistStub.vbs`  

5. At the command prompt, type the following command, and then press ENTER:  

   -   `UndeployStub.vbs`  

6. At the command prompt, run the following command  

    SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"  

    This sets the path to find the BAM utilities.  

   > [!NOTE]
   >  If you are using a 64-bit computer, type `%ProgramFiles(x86)%` instead of `%ProgramFiles%`.  

7. At the command prompt, change the directory to %BTSSolutionsPath%\SO\BTSSoln\BAM, and then run the following command:  

   -   `bm remove-all -DefinitionFile:ServiceLevelTracking.xml`  

8. At the command prompt, change the directory to \<*Enterprise Single Sign-On Install Directory*\>, and then run the following command:  

   -   `ssomanage -tickets no no`  

9. At the command prompt, run the following command to delete the WoodgroveBank.CustomerService SSO Affiliated application:  

    -   `ssomanage -deleteapp WoodgroveBank.CustomerService`  

10. At the command prompt, run the following commands to delete the Web sites used by the stub version. For more information about iisvdir.vbs, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).  

    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub`  

    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP`  

    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions`  

    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker`  

11. Start Internet Information Services (IIS) Manager as follows: Click **Start**, point to **All Programs**, point to **Administration Tools**, and then click **Internet Information Services (IIS) Manager**.  

    -   Expand the **Application Pools**, right-click the application pool you crated for the previous Web applications, click **Delete**, and then click **OK** in the confirmation dialog box.  

12. Click **Start**, point to **Control Panel**, click **Add or Remove Programs**, and then uninstall the IBM WebSphere MQ Client for Windows.  

13. Start **Visual Studio Command Prompt** and then run the following command to delete the amqmdnet.dll you installed for the stub version.  

    -   `gacutil /u amqmdnet`  

##  <a name="step5"></a> Prepare the back-end systems for the Service Oriented Solution to access  

1. Install IBM WebSphere MQ for Windows Server on the local computer.  

   1.  Keep all the default settings. Set up the **Default Configuration** at the end of the **Prepare WebSphere MQ Wizard**. The queue manager is named as QM_\<*your computer name*\>.  

   2.  Install the Fix Pack 10 (CSD10). Keep all the default settings.  

2. Install the MQSeries Agent.  

   1.  Rerun the BizTalk Server setup program.  

   2.  On the **Program Maintenance** page, select **Modify**, and then click **Next**.  

   3.  On the **Component Installation** page, expand the **Additional Software** node, and then select **MQSeries Agent**.  

   4.  On the **Completion** page, make sure that **Launch BizTalk MQSeries Agent Configuration Wizard** is not selected.  

   > [!NOTE]
   >  The **MQSeries Agent** check box is activated only after the IBM WebSphere MQ for Windows is installed.  

3. Open a **Visual Studio Command Prompt**, change the directory to the \<*IBM MQSeries Installation Directory*\>\bin folder, and then run the following command:  

   -   `gacutil /i amqmdnet.dll`  

4. Install Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] if you want to install Microsoft Host Integration Server 2004 to access the mainframe. In the setup program, on the **Options** page, select **Visual C# .NET**, and then clear other components checkboxes. You don't need to install other components than the **Visual C# .NET**.  

   > [!NOTE]
   >  The TI Designer in Host Integration Server 2004 requires [!INCLUDE[btsVStudioNet2003](../includes/btsvstudionet2003-md.md)].  

5. Install and configure Microsoft Host Integration Server 2004 if you have a mainframe to be accessed. Keep all the default settings.  

#### Create the MQSeries queues  

1.  Open the WebSphere MQ Explorer, expand **Queue Managers**, and then expand the queue manager in which you want to create the queues. Typically, a queue manager is named as QM_\<*your computer name*\>.  

2.  In the WebSphere MQ Explorer, right-click **Queues**, point to **New**, click **Local Queue**, and then create the following local queues for the adapter version of the solution:  

    -   AdapterSOAInputQueue  

    -   AdapterSOAOutputQueue  

    > [!NOTE]
    >  The queues can share an MQSeries cluster, but they are not required to do so.  

    > [!NOTE]
    >  MQSeries queue manager names and queue names are case sensitive.  

3.  Repeat the previous step to create the following local queues for the inline version:  

    -   InlineSOAOutputQueue  

    -   InlineSOAInputQueue  

4.  Repeat the previous step to create the following local queues for the Payment Tracker simulator. (The Payment Tracker simulator is used in both the adapter and inline versions):  

    -   LastPaymentsInputQueue  

    -   LastPaymentsOutputQueue  

#### Complete configuration of the MQSeries adapter  

1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk MQSeries Agent Configuration Wizard**.  

2. On the **Welcome** page, click **Next**.  

3. On the **Application Identity** page, select **This User**, and then enter the user name and password. The COM+ application for the MQSeries Agent will run under this user account. For this walkthrough, use the same user account that the BizTalk service is using. If it is not, the user accounts for BizTalk services hosting the MQSeries Adapter must be added to the **CreatorOwner** role of the COM+ application.  

4. Click **Yes** on the **MQSConfigWiz** dialog box, if prompted that the user account that you entered in the previous step has the administrative privilege.  

5. On the **Name of Role** page, click **Next**.  

6. On the **Creating the MQSAgent COM+ Application** page, click **Next**, and then click **Finish** on the **Completion** page.  

#### Configure the mainframe CICS application  

1.  Using Notepad, open the bizcbl.txt and its "copy book" (MainFrameProgramVTCS2Description.txt) in the %BTSSolutionsPath%\SO\MFAccess\HISTIComponent folder, and then review the contents.  

    -   Bizcbl.txt includes the COBOL procedure returning the randomized account statements from account number input.  

    -   MainFrameProgramVTCS2Descriptoin.txt contains COMMAREA which describes the input and output data information. COMMAREA is a block of contiguous memory used to pass data back and forth between called and calling programs.  

    > [!NOTE]
    >  You can also use the copy book to generate the Transaction Integrator (TI) metadata file using Visual Studio with the TI Designer plug-in.  

    > [!NOTE]
    >  Although the following steps are crucial to the successful deployment, they are not usually performed by the BizTalk Server developer. You must rely on the mainframe personnel to properly configure the mainframe environment. The software required for this walkthrough is usually installed in the most mainframe environments. For more information about the minimum mainframe operating system environment, see the Host Integration Server documentation.  

2.  Copy the COBOL code to the host by method like FTP.  

3.  Compile the COBOL code and copy book. The following code shows a sample of Job Control Language (JCL) for the COBOL compiler.  

    ```  
    //COB      EXEC PGM=IGYCRCTL,  
    //            PARM=&COBPARM,  
    //            REGION=&REG  
    //STEPLIB  DD DSN=&COMPINDX..SIGYCOMP,DISP=SHR  
    //SYSLIB   DD DSN=&INDEX..SDFHCOB,DISP=SHR  
    //         DD DSN=&INDEX..SDFHMAC,DISP=SHR  
    //         DD DSN=&HLQ..&COMP..COBCOPY,DISP=SHR  
    //SYSPRINT DD SYSOUT=&OUTC  
    //*SYSPRINT DD DSN=&&INPUT,DISP=(,PASS),UNIT=SYSDA,  
    //*         SPACE=(TRK,(100,50)),  
    //*         DCB=(DSORG=PS,LRECL=121,BLKSIZE=2420,RECFM=FBA)  
    //SYSIN    DD DSN=&&SYSCIN,DISP=(OLD,DELETE)  
    //SYSLIN   DD DSN=&&LOADSET,  
    //            DISP=(MOD,PASS),  
    //            UNIT=&WORK,  
    //            SPACE=(80,(250,100))  
    //SYSUT1   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT2   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT3   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT4   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT5   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT6   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT7   DD UNIT=&WORK,SPACE=(460,(350,150))  
    ```  

4.  Link edit the compiled source to create the executable. The following code shows a sample of JCL for COBOL link edit.  

    ```  
    //LKED     EXEC PGM=IEWL,REGION=&REG,  
    //            PARM=&LNKPARM,COND=(5,LT,COB)  
    //SYSLIB   DD DSN=&INDEX..SDFHLOAD,DISP=SHR  
    //         DD DSN=CEE.SCEELKED,DISP=SHR  
    //         DD DSN=&TCPINDX..SEZATCP,DISP=SHR  
    //SYSLMOD  DD DSN=&LMINDX..&COMP..LOADLIB,DISP=SHR  
    //SYSUT1   DD UNIT=&WORK,  
    //            DCB=BLKSIZE=1024,  
    //            SPACE=(1024,(200,20))  
    //SYSPRINT DD SYSOUT=&OUTC  
    //SYSLIN   DD DSN=&&LOADSET,DISP=(OLD,DELETE)  
    //         DD DSN=&&COPYLINK,DISP=(OLD,DELETE)  
    ```  

5.  Configure the CICS mainframe application.  

    -   In this step, the mainframe systems programmer or CICS developer must install TCPIPSERVICE, Session, Connection, Transaction, and Program resource definitions.  

    -   You should consult with mainframe administrators to get an IP address, port number, and a Link to Program name that you can access.  

        > [!NOTE]
        >  This walkthrough assumes that the mainframe uses a CICS application server and that the programming model for the transaction is TCP/IP (Enhanced Listener Mode (ELM) Link).  

##  <a name="step7"></a> Configure the Web server for Secure Socket Layers (SSL)  

#### Install Certificate Services  

1.  Click **Start**, point to **Control Panel**, and then click **Add or Remove Programs**.  

2.  In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.  

3.  In the **Windows Components Wizard**, select the **Certificate Services**, click **Next**, and then follow the on-screen instructions to complete the installation.  

#### Create a certificate request  

1.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, click **Properties**, click the **Directory Security** tab, and then click **Server Certificate**.  

2.  On the **Welcome** page of the **Web Server Certificate Wizard**, click **Next**.  

3.  On the **Service Certificate** page, select **Create a new certificate**, and then click **Next**.  

4.  On the **Delayed or Immediate Request** page, click **Prepare the request now, but send it later**, and then click **Next**.  

5.  On the **Name and Security Settings** page, keep all the default settings, and then click **Next**.  

6.  On the **Organization Information** page, type your company's organization and organizational unit names, and then click **Next**.  

7.  On the **Your Site's Common Name** page, type your computer name in the **Common name** box, and then click **Next**.  

8.  On the **Geographical Information** page, fill out your geographical information, and then click **Next**.  

9. On the **Certificate Request File Name** page, type `c:\certreq.txt` in the **File name** box, and then click **Next**.  

10. On the **Request File Summary** page, click **Next**, and then click **Finish** on the **Completion** page.  

#### Submit the certificate request to the Certification Authority  

1.  In Internet Explorer, in the Address box, type `http://localhost/certsrvt`, and then press ENTER.  

2.  On the **Welcome** page, click **Request a Certificate**, and then click **Advanced certificate request** on the **Request a Certificate** page.  

3.  On the **Advanced Certificate Request** page, click **Submit a certificate request using a base64 encoded PKCS #10 file or a renewal request using a base64 encoded PKCS #7 file**.  

4.  Copy all the text from the c:\certreq.txt that you created in the procedure "To create a certificate request", paste it to the **Saved Request** box on the **Submit a Certificate Request or Renewal Request** page, and then click **Submit**.  

#### Issue a certificate using Certification Authority management tool  

1.  Click **Start**, point to **Administrative Tools**, and then click **Certification Authority**.  

2.  In the **Certification Authority** console, expand your certification authority's name, expand the **Pending Request**, right-click the certificate request that you submitted in the previous step, point to **All Tasks**, and then click **Issue**.  

3.  Close the **Certification Authority** console.  

#### Download the certificate to the Web server  

1.  In Internet Explorer, in the Address box, type `http://localhost/certsrvt`, and then press ENTER.  

2.  On the **Welcome** page, click **View the status of a pending certificate request**.  

3.  On the **View the Status of a Pending Certificate Request** page, click the certificate **request** that you created in the procedure "To create a certificate request".  

4.  On the **Certificate Issued** page, select either of the encoding schemes, and then click **Download certificate**.  

5.  On the **Security Warning** dialog box, click **Save**, and then save the certificate as c:\certnew.cer.  

#### Install the certificate to the Web server  

1.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site** for which you created the certificate request, and then click **Properties**.  

2.  On the **Properties** dialog box, click the **Directory Security** tab, and then click **Server Certificate**.  

3.  On the **Welcome** page of the **Web Server Certificate Wizard**, click **Next**.  

4.  On the **Pending Certificate Request** page, select **Process the pending request and install the certificate**, and then click **Next**.  

5.  On the **Process a Pending Request** page, type `c:\certnew.cer` in the **Path and file name** text box, and then click **Next**.  

6.  Click **Next** on the **SSL Port** page, click **Next** on the **Certificate Summery** page, and then click **Finish** on the **Confirmation** page.  

    > [!NOTE]
    >  In this walkthrough you don't need to install the server certificate to the Trusted Root Certification Authorities store on the local computer because both Certificate Services and Web server are installed on the same computer.  

##  <a name="step9"></a> Create the Web services for the back-end systems  

1.  In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **New**, and then select **Application Pool**.  

    > [!NOTE]
    >  The service oriented solution accesses the mainframe through this Web service.  

2.  On the **Add New Application Pool** dialog box, enter the **Application pool ID** (any value), and then click **OK**.  

3.  In the **Internet Information Services (IIS) Manager**, right-click the application pool that you just created, and then select **Properties**.  

4.  On the **Properties** page, click the **Identity** tab, select **Configurable**, enter the **User name** and **Password**, and then click **OK**. For this walkthrough, use the same user account that the BizTalk service is using.  

#### Create the PendingTransactions Web service for runtime  

1.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.  

     Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:  

     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions  

     PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\MFAccess\PendingTransactions  

     Access Permissions = Read, Run scripts  

2.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions, and then click **Properties**.  

    1.  In the **Directory Security** tab, click **Edit** to modify **Authentication and access control**. Select **Basic authentication (password is sent in clear text)**, and clear other **Authentication access** checkboxes. Click **OK** to close the **Authentication Methods** dialog box.  

    2.  In the **Directory Security** tab, click **Edit** under the **Secure Communication** group box, and then check **Require secure channel (SSL)** in the **Secure Communications** dialog box.  

    3.  In the **Virtual Directory** tab, set the **Application Pool** to the application pool that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".  

#### Create the PendingTransactions Web service for development environment  

1. In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.  

    Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:  

    Alias = PendingTransactions  

    PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\MFAccess\PendingTransactions  

    Access Permissions = Read, Run scripts  

2. In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click PendingTransactions, and then click **Properties**.  

   1. In the **Directory Security** tab, click **Edit** to modify **Authentication and access control**. Select **Enable anonymous access**. Click **OK** to exit.  

      > [!NOTE]
      >  The PendingTransactions Web application for development environment will be used by [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. You don't need this Web application for production environment.  

   2. In the **Virtual Directory** tab, set the **Application Pool** to the application pool that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".  

#### Create the Stub SAP Web service  

1.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.  

     Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:  

     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP  

     PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP  

     Access Permissions = Read, Run scripts  

2.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, click **Properties**, and then modify the settings as follows:  

    1.  In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".  

    2.  In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**. Click **OK** to exit.  

##  <a name="step11"></a> Create the TI component for the Service Oriented Solution  

#### Create a COM+ application for the TI component  

1.  At a command prompt, run %systemroot%\system32\com\comexp.msc.  

2.  In **Component Services** console, expand **Component Services**, expand **Computers**, expand **My Computer**, right-click **COM+ Application**, point to **New**, and then click **Application**.  

    1.  On the **Welcome** page, click **Next**, and then click **Create an empty application** on the **Install or Create a New Application** page.  

    2.  Type `BTSScn SO TI Component` in the **Enter a name for the new application** box, select **Server application** as **Activation type**, and then click **Next**.  

    3.  In the **Account** group box of the **Set Application Identity** page, select **This user**, and then type the user name and password in the **User** and **Password** boxes. The new COM+ application will run under this user account. This user account must be a member of local HIS Runtime Users group. For this walkthrough, use the same user account that the BizTalk service is using.  

    4.  On the **Add Application Roles** page, click **Next**.  

    5.  On the **Add Users to Roles** page, expand **CreatorOwner**, click **Users**, and then click **Add**.  

    6.  On the **Select Users or Groups** dialog box, select a user account that will be used for accessing the mainframe. For this walkthrough, add UserID local account.  

        > [!NOTE]
        >  To access the CICS transaction through the TI component, you can use the COM+ application or the Web application hosting the .NET Remoting component. This walkthrough uses the COM+ application and COM Interop for TI components to access the mainframe to improve performance.  

    7.  On the **Completion** page, click **Finish**.  

#### Create a Remote Environment to access the mainframe  

1.  Click **Start**, point to **All Programs**, point to **Microsoft Host Integration Server 2004**, and then click **TI Manager**.  

2.  In the **TI Manager** console, click **Transaction Integrator (Configuration)**, expand **Windows Initiated Processing**, right-click **Remote Environments**, point to **New**, and then click **Remote Environment**.  

    1.  On the **Welcome** page, click **Next**.  

    2.  On the **Configure a New Remote Environment** page, type the **Remote Application Name**, and then click **Next**. For this walkthrough, use Mainframe_TCP for the name.  

    3.  On the **Configure Host Environment and Programming Model** page, select **CICS** for the **Target host** and **ELM Link** for the **Programming model**, and then click **Next**.  

    4.  On **the Configure Endpoint TCP/IP** page, type the IP address for your mainframe in the **IP/DNS address** box, and then click **Edit** to add the port number. Your HIS COM will access the transactions through the endpoint address.  

    5.  On the **Completion** page, click **Finish**.  

#### Create the TI Component for the Service Oriented Solution  

1.  Click **Start**, point to **All Programs**, point to **Microsoft Host Integration Server 2004**, and then click **TI Manager**.  

2.  In the **TI Manager** console, click **Transaction Integrator (Configuration)**, click **Windows Initiated Processing**, and then click **Objects**. Right-click **Objects**, click **New**, and then click **Object**.  

    1.  On the **Welcome** page, click **Next**.  

    2.  On the **Specify Or Locate An Object** page, click **Browse**, choose the SOHISTIUsingCOM.TLB in the %BTSSolutionsPath%\SO\MFAccess\HISTIComponent folder, and then click **Next**.  

    3.  On the **Define Environment Characteristics for The COM Object** page, select **BTSScn SO TI Component** for the **COM+ application**, and then click **Next**.  

    4.  On the **Define Remote Environment** page, select the remote environment that you created in the previous procedure for the **Remote environment, and then click Next.**  

    5.  On the **Creation of WIP Objects** page, click **Next**, and then click **Finish** on the **Completion** page.  

#### Test the connectivity to the mainframe  

1.  In Windows Explorer, browse to the %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester folder, and then double-click the Interop.SOHISTIUsingCOM.dll.reg file. This adds registry values for the HISTISimpleTester application to call the TI component through the Runtime Callable Wrapper (RCW).  

2.  In Windows Explorer, browse to the %BTSSolutionsPath%\SO\MFAccess\ folder, and then run SetupMFAccess.bat.  

3.  In Windows Explorer, navigate to the %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester\bin\Debug folder, and then run BTSScnSOHISTIComponentSimpleTester.exe.  

    -   In the HISTISimpleTester application, click **Call Mainframe Program - Using COM**. It returns five records from the COBOL application running on the mainframe.  

##  <a name="step13"></a> Create the virtual directories for the orchestration Web services  

1.  In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **New**, and then select **Application Pool**.  

    1.  On the **Add New Application Pool** dialog box, enter the **Application pool ID** (any value), and then click **OK**.  

    2.  Right-click the application pool that you just created, and then select **Properties**.  

    3.  On the **Properties** page, click the **Identity** tab, select **Configurable**, enter the **User name** and **Password**, and then click **OK**. For this walkthrough use the same user account that the BizTalk service is using.  

    > [!NOTE]
    >  This user must have permission to execute the Orchestration Proxy Web service, and must be added to one of the BizTalk Server Administrators, SSO Administrators, or SSO Affiliated Administrators groups  

2.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.  

     Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:  

     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter  

     PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Adapter  

     Access Permissions = Read, Run scripts  

3.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter, click **Properties**, and then modify the settings as follows:  

    1.  In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> that you created in the previous step.  

    2.  In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes. Click **OK** to exit.  

4.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.  

     Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the inline version:  

     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline  

     PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Inline  

     Access Permissions = Read, Run scripts  

5.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline, click **Properties**, and then modify the settings as follows:  

    1.  On the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> you just created.  

    2.  Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes. Click **OK** to exit.  

##  <a name="step15"></a> Build the Service Oriented Solution  

-   At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln, type `SetupBTSSoln.bat`, and then press ENTER. The SetupBTSSoln.bat performs the following tasks:  

    -   Creates a unique strong name key (SNK) for signing the assemblies of the SO Solution.  

    -   Extracts the public key token from the SNK and updates the binding files with the public token.  

    -   Builds the SO solution.  

    -   Builds the SSOApplicationConfig in the %BTSSolutionsPath%\Common folder.  

##  <a name="step17"></a> Create the SSO affiliate applications  

1. Open a command prompt, and then change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.  

2. At the command prompt, open the PendTransAffApp.xml using Notepad, and review it. No changes to this file are necessary.  

   > [!NOTE]
   >  The PendTransAffApp.xml file defines the SSO affiliate application, WoodgroveBank.PendingTransactions, for the Pending Transactions back-end system. It also defines the user and administrative groups for the SSO affiliate application. For this walkthrough, use **BizTalk Application Users** and **BizTalk Server Administrators**.  
   >   
   >  If you want to use different groups for the SSO affiliate application, you need to create Windows groups (with any name) in the Active Directory, and then change the **appAdminAccount** and **appUserAccount** nodes in the PendTransAffApp.xml. If you do this, you should set the value for **groupApp** attribute of **flags** node to "yes".  
   >   
   >  For more information about SSO affiliate applications, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).  

3. At the command prompt, open the PendTransUserMap.xml file using Notepad, and then make the following edits:  

   ```  
   <mapping>  
     <windowsDomain><DomainName></windowsDomain>  
     <windowsUserId><UserID></windowsUserId>  
     <externalUserId><ExternalUserID></externalUserId>  
   </mapping>  
   ```  

   > [!NOTE]
   >  The PendTransUserMap.xml file contains the user mappings for the Pending Transactions back-end system.  

   > [!NOTE]
   >  For the **externalUserId** node, use the external user ID for the Pending Transactions back-end system. For this walkthrough, use UserID for the external ID.  

   > [!NOTE]
   >  For the **windowsUserId** node, enter the user name which the **externalUserId** will map to. You can use both a domain group and a domain user account. This user must be a member of the group that will be allowed to use the Pending Transactions back-end system. For this walkthrough, use the user name of the BizTalk service.  

   > [!NOTE]
   >  For the **windowsDomain** node, enter the domain name of the **windowsUserId**.  

4. At the command prompt, open the PmntTrckAffApp.xml file using Notepad, and review the contents of the file. No changes to this file are necessary.  

   > [!NOTE]
   >  The PmntTrckAffApp.xml file defines the SSO affiliate application, WoodgroveBank.PaymentTracker, for the Payment Tracker back-end system.  

5. At the command prompt, open the PmntTrckUserMap.xml file using Notepad, and then make the following edits:  

   ```  
   <mapping>  
     <windowsDomain><DomainName></windowsDomain>  
     <windowsUserId><UserID></windowsUserId>  
     <externalUserId><ExternalUserID></externalUserId>  
   </mapping>  
   ```  

   > [!NOTE]
   >  The Payment Tracker SSO affiliated application will be used for the MQSeries Adapter and the mapped external user ID/password are sent through MQSeries header properties. The MQSeries Server validates only the BizTalk service account, under which MQSeries Adapter is running. It doesn't validate any external user credential.  
   >   
   >  For more information about SSO affiliated applications for the MQSeries Adapter, see [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).  

   > [!NOTE]
   >  The PmntTrckUserMap.xml file contains the SSO user mappings for the Payment Tracker back-end system. The Payment Tracker simulator program simulates both success and failure conditions for user authentication.  
   >   
   >  The program successfully authenticates all user IDs that begin with the letters **PT** (for example, **PTUserID**), and fails to authenticate any user IDs that do not begin with **PT**. This enables you to choose the appropriate user ID depending on the condition that you would like to test. You can also repeat the entire **mapping** node for each user ID and define multiple mappings in the same file.  

   > [!NOTE]
   >  For the **externalUserId** node, enter the external user ID for the Payment Tracker back-end system. For this walkthrough, use PTUserID for the external ID.  

   > [!NOTE]
   >  For the **windowsUserId** node, enter the user name which the **externalUserId** will map to. This user must be a member of the group that will be allowed to use the Payment Tracker back-end system. For this walkthrough, use the user name of the BizTalk service.  

   > [!NOTE]
   >  For the **windowsDomain** node, enter the domain name of the **windowsUserId**.  

6. At the command prompt, open the ConfigStoreApp.xml file using Notepad, and then review the contents of the file.  

    This file defines the configuration store application in SSO that the scenario uses to keep configuration parameters. Some of the configuration parameters include the Timeout value when communicating with SAP (for both the adapter and inline versions) and the name of the queue manager and queues to use when using the inline version. No changes to this file are necessary.  

7. At the command prompt, open the SetConfigValuesInSSO.cmd file using Notepad, review and change the contents of the file as the following table.  

   > [!NOTE]
   >  This command file sets the values for the configuration parameters in the SSO database. It contains several set commands that assign the values to local variables in the beginning of the command file.  
   >   
   >  The SAPAdapterTimeout, PendingTransactionsAdapterTimeout, and PaymentTrackingAdapterTimeout values are used in the adapter version. The remaining values are used in the inline version.  

   > [!NOTE]
   >  You can enter " " (two double quotes) for the default values marked \<User Specified\> in the following table.  

   |                Parameter                 |                                                 Default Value                                                 |                                                                                                                Description                                                                                                                 |
   |------------------------------------------|---------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            SAPAdapterTimeout             |                                                     20000                                                     |                                                                                        Max timeout (millisecond) for a request to the SAP back-end                                                                                         |
   |             SAPInlineTimeout             |                                                     20000                                                     |                                                                                        Max timeout (millisecond) for a request to the SAP back-end                                                                                         |
   |            SAPInlineHostName             |                                              \<User Specified\>                                               |                                                                                                          SAP back-end identifier                                                                                                           |
   |          SAPInlineClientNumber           |                                              \<User Specified\>                                               |                                                                                                             SAP Client number                                                                                                              |
   |          SAPInlineSystemNumber           |                                              \<User Specified\>                                               |                                                                                                             SAP System number                                                                                                              |
   |            SAPInlineUserName             |                                              \<User Specified\>                                               |                                                                                             The user name used to connect to the SAP back-end                                                                                              |
   |            SAPInlinePassword             |                                              \<User Specified\>                                               |                                                                                              The password used to connect to the SAP back-end                                                                                              |
   |    PendingTransactionsAdapterTimeout     |                                                     20000                                                     |                                                                                 Max timeout (millisecond) for a request to the Pending Transactions server                                                                                 |
   |     PendingTransactionsInlineTimeout     |                                                     20000                                                     |                                                                                 Max timeout (millisecond) for a request to the Pending Transactions server                                                                                 |
   |       PendingTransactionsInlineURL       | https://\<*your computer name*\>/Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions/PendTransWS.asmx |              URL of the Pending Transactions service. \<*Your computer name*\> must match the **common name** in the procedure "To create a certificate request". You must not use "localhost" for \<*Your computer name*\>.               |
   | PendingTransactionsInlineSSOAffiliateApp |                                       WoodgroveBank.PendingTransactions                                       |                                                                                                 Pending Transactions SSO application name                                                                                                  |
   |      PaymentTrackingAdapterTimeout       |                                                     20000                                                     |                                                                                   Max timeout (millisecond) for a request to the Payment Tracking system                                                                                   |
   |       PaymentTrackingInlineTimeout       |                                                     20000                                                     |                                                                                   Max timeout (millisecond) for a request to the Payment Tracking system                                                                                   |
   |      PaymentTrackingInlineQManager       |                          \<User Specified\> (Typically QM_\<*your computer name*\>).                          |                                                                                                        MQSeries Queue Manager name                                                                                                         |
   | PaymentTrackingInlineMQChannelDefinition |                                  " " (need to enter the two double quotes).                                   | Empty string if local, or formatted channel name of the remote MQ server. If you keep all default settings in configuring IBM WebSphere MQ, the channel definition will be S__\<*your computer name*\>/TCP/\<*your computer name*\>(1414). |
   |    PaymentTrackingInlineRequestQueue     |                                            LastPaymentsInputQueue                                             |                                                                                              The MQ Queue name for payment tracking requests                                                                                               |
   |    PaymentTrackingInlineResponseQueue    |                                            LastPaymentsOutputQueue                                            |                                                                                              The MQ Queue name for payment tracking responses                                                                                              |
   |   PaymentTrackingInlineSSOAffiliateApp   |                                         WoodgroveBank.PaymentTracker                                          |                                                                                                   Payment tracking SSO application name                                                                                                    |
   |           StubSAPWebServiceURL           |                http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP/StubSAPWS.asmx                |                                                                                          The stub Web service URL of the Credit Limit SAP system                                                                                           |


8. At the command prompt, run the following command to set the PATH environment:  

   -   `SET PATH=%PATH%;"%CommonProgramFiles%\Enterprise Single Sign-On"`  

9. At the command prompt, run the CreateInitialConfigInSSO.cmd. It creates the SSO Affiliate Applications, the SSO configuration store application, and the user mappings for the affiliate applications. Then, it executes the SetConfigValuesInSSO.cmd to store configuration values in the SSO configuration store application.  

10. At the command prompt, run the following command to set the user credential for the Pending Transactions affiliate application. Use the \<**DomainName**\> and \<**UserID**\> defined in the PendTransUserMap.xml for the \<WindowsDomain\>\\<WindowsUserId\>. This command asks you to enter the password of the external user, UserID, used in this walkthrough.  

    -   `ssomanage -setcredentials <WindowsDomain>\<WindowsUserId> WoodgroveBank.PendingTransactions`  

11. At the command prompt, run the following command to set the user credential for the Payment Tracker affiliate application. Use the \<**DomainName**\> and \<**UserID**\> defined in the PmntTrckUserMap.xml for the \<WindowsDomain\>\\<WindowsUserId\>. This command asks you to enter the password of the external user, PTUserID, used in this walkthrough.  

    > [!NOTE]
    >  The Payment Tracker simulator doesn't validate the external user credential. You can enter any password for the PTUserID.  

    -   `ssomanage -setcredentials < WindowsDomain >\< WindowsUserId > WoodgroveBank.PaymentTracker`  

##  <a name="step19"></a> Deploy the BAM definition file for the Service Oriented Solution  

1. Open a command prompt, type the following command, and then press ENTER to set the path to find the BAM utilities:  

   - SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"  

2. At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\BAM, type the following command, and then press ENTER:  

   -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  

##  <a name="step21"></a> Deploy the Service Oriented Solution  

#### Update the binding files for the Service Oriented Solution  

1. At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, open the Deployallbinding.xml using Notepad, and then make the following edits:  

   -   Change the name of the server in the SET MGMT_DB_SERVER and MBMT_DB to the name of the server and database that BizTalk Server is using.  

   -   Change the value of the SOLNDIR variable to "%BTSSolutionsPath%\SO\BTSSoln".  

2. At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Bindings folder.  

3. For the adapter version, open the AdapterSOAOrchBindings.xml using Notepad, and then edit as follows:  

   - Replace all occurrences of *_MQ_SERVER_NAME\\*\_ with the MQSeries Server name.  

   - Replace all occurrences of *_MQ_QMANAGER_NAME\\*\_ with the MQSeries Queue Manager name.  

   - Replace all occurrences of *_PT_WS_SERVER_NAME\\*\_ in the string "\<Address\>https://\_*PT_WS_SERVER_NAME\\*\_" with the server name where the Pending Transactions Web service is deployed. The server name must match the **common name** in the step, "To configure the Web server for SSL". You shouldn't use localhost.  

   > [!NOTE]
   >  The binding file, AdapterSOAOrchBindings.xml, uses the stub Web service for:  
   > 
   > 1. The Credit Limit back-end SAP system.  
   >    2.  The MQSeries adapter to integrate with the Payment Tracking back-end system.  
   >    3.  The Pending Transactions Web service to call the HIS TI .NET component to integrate with the mainframe back-end system.  
   > 
   >    If you aren’t using the mainframe, you must use the stub Web service to generate data for the Pending Transactions system.  

4. For the inline version, open the InlineSOAOrchBindings.xml using Notepad, and then edit as follows:  

   - Replace all occurrences of *_MQ_SERVER_NAME\\*\_ with the MQSeries Server name.  

   - Replace all occurrences of *_MQ_QMANAGER_NAME\\*\_ with the MQSeries Queue Manager name.  

#### Deploy the Service Oriented solution  

-   At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER.  

    -   `Deployallbinding.cmd`  

    > [!NOTE]
    >  The Deployallbinding.cmd creates the BizTalk application named BTSScn.SO.CustomerService and imports binding files for the adapter and inline versions.  

##  <a name="step23"></a> Configure the stub Pending Transactions Web Services when a mainframe is not available  

#### Configure the stub Pending Transactions Web service (for using the adapter version without a mainframe)  

1.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.  

     Using the **Virtual Directory Creation Wizard**, create the following virtual directory for stub Pending Transactions Web service for the adapter version:  

     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions  

     PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans  

     Access Permissions = Read, Run scripts  

2.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows using the **Properties** dialog box.  

    1.  In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> you created in the step, "To create the virtual directories in IIS for the solution".  

    2.  In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**. Click **OK** to exit.  

3.  In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Applications**, expand BTSScn.SO.CustomerService, expand **Send Ports**, right-click **PendingTransactionSolicitResponsePort**, and then click **Properties**.  

    1.  In the **General** page, click **Configure** to display the **Transport Properties** dialog box, and then modify the **Web Service URL** to the stub Pending Transaction Web service, for example:  

         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  

    2.  Close all of the dialog boxes.  

#### Configure the stub Pending Transactions Web service (for using the inline version without a mainframe)  

1.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.  

     Using the **Virtual Directory Creation Wizard**, create the following virtual directory for stub Pending Transactions Web service for the adapter version:  

     Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions  

     PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans  

     Access Permissions = Read, Run scripts  

2.  In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows:  

    1.  In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> you created in the step, "To create the virtual directories in IIS for the solution".  

    2.  In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**. Click **OK** to exit.  

3.  Open a command prompt, and then change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.  

4.  At the command prompt, open the SetConfigValuesInSSO.cmd file using Notepad, and then set the value of the **PendingTransactionsInlineURL** to the URL of the stub Pending Transaction Web Service.  

    -   `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  

5.  At the command prompt, type `SetConfigValuesInSSO.cmd`, and then press ENTER.  

##  <a name="step25"></a> Start the Service Oriented Solution  

1.  Open a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER to start all orchestrations for the inline and adapter versions.  

    -   `startAll.vbs`  

2.  Run the service-oriented solution. For more information about running the solution, see [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).  

## Next Steps  
 You test the inline and adapter version of the service-oriented solution in [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).  

## See Also  
 [Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md)   
 [How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)   
 [Developer Machine Setup for the Service Oriented Solution](../core/developer-machine-setup-for-the-service-oriented-solution.md)