---
title: "How to Configure a Workflow Foundation Application for Interception | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c82e83f-9dbd-4325-9f30-778eba892296
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a Workflow Foundation Application for Interception
You must install the BAM interceptor software and configure your application to use the [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] interceptor service before you can begin collecting BAM activity data. It is assumed that you have successfully installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and its dependencies and have created at least one BizTalk group.  
  
## Installing the BAM-Eventing Software  
 Before you can configure your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application to use the BAM interceptor for [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], you must install the BAM-Eventing software by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Setup program. For more information about installing the BAM-Eventing software and registering the performance counters, see [Installing the BAM-Eventing Software](../core/installing-the-bam-eventing-software.md).  
  
## Configuring a Windows Workflow Foundation Application for Tracking  
 Four tasks must be completed before your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application can begin writing BAM event information:  
  
- An observation model must be created by using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM tools and then deployed by using the BAM Manager command-line tool (bm.exe).  
  
- An interceptor configuration file must be created and deployed by using the BAM Manager command line-tool (bm.exe).  
  
- The user running the host application must be a member of the appropriate BAM activity event writer (bam_\<activity\>_EventWriter) SQL Server roles to enable the application to read the interceptor configuration information and write to the BAM activities.  
  
- The App.config file or the application itself must be modified to load the BAM tracking service and then restart the application.  
  
  Only after these tasks have been successfully completed will events begin appearing in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM database.  
  
### Deploying an Observation Model  
 You must have an observation model deployed before you can deploy an interceptor configuration file or capture BAM activities in your application.  
  
##### To deploy an observation model by using bm.exe  
  
1. Click **Start** and then click **Run** to open the Windows command prompt.  
  
2. Type **cmd** in the **Open** field, and then click **OK**.  
  
3. Use the change directory command to move to the directory containing the observation model to deploy. For example, **cd c:\businessprocess\Orders**.  
  
4. Deploy the observation model by using bm.exe:  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\BM.exe deploy-all -definitionfile:\<*definitionfile.xml*\>  
  
    Make sure you replace \<*definitionfile.xml*\> with the name of the observation file you want to deploy. For more options see [Interceptor Management Commands](../core/interceptor-management-commands.md).  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
5. Type **Exit**, and then press ENTER to close the command prompt.  
  
### Deploying an Interceptor Configuration File  
 You must deploy an interceptor configuration file before your application can capture BAM activities.  
  
##### To deploy an interceptor configuration file by using bm.exe  
  
1. Click **Start** and then click **Run** to open the Windows command prompt.  
  
2. Type **cmd** in the **Open** field, and then click **OK**.  
  
3. Use the change directory command to move to the directory containing the interceptor configuration file to deploy. For example, **cd c:\businessprocess\Orders**.  
  
4. Deploy the interceptor configuration file by using bm.exe:  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\BM.exe deploy-interceptor -filename:\<*icfile.xml*\>  
  
    Make sure you replace \<*icfile.xml*\> with the name of the interceptor configuration file you want to deploy.  
  
   > [!NOTE]
   >  You can use the **-Force:True** flag to override existing event sources with the same name(s) as those in your interceptor configuration file. If you do so, make sure you back up the existing configuration by using the **get-interceptor** command. Using the -Force:True flag could delete any interceptor configurations that reference the event sources being overwritten.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
5. Type **Exit**, and then press ENTER to close the command prompt.  
  
   If you have already deployed your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application, the new configuration will not be loaded until the next polling interval. However, if you configure your application and restart it, the configuration will be picked up immediately.  
  
### Adding the User to the Appropriate BAM Activity Role  
 The BAM Interceptor Framework uses per-activity SQL Server roles to control access to activities and configuration information. You must add the user account running your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application to the appropriate BAM activity role(s) in the BAM Primary Import database.  
  
### Configuring the Application to Load the BAM Tracking Service  
 There are three scenarios for loading the BAM tracking service in your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application:  
  
- If your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application already uses WorkflowRuntime to load a [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] configuration section, you can added BAM tracking service information to the existing section.  
  
- If your [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application does not use WorkflowRuntime to load a [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] configuration section, you will have to add code to load a custom section from your application configuration file. You will have to create the section and add the BAM tracking service information to it.  
  
- If you prefer to hard-code the configuration, you can use the [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] API to programmatically load the tracking service without a configuration file, or to load the configuration from a custom source.  
  
  When configuring the [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] application, note the following considerations:  
  
- The [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] interceptor supports only one BamTrackingService per one WorkflowRuntime.  
  
- The [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] interceptor supports multiple BamTrackingService instances per application domain.  
  
  -   N number of BamTrackingService is supported for N number of WorkflowRuntime.  
  
- The interceptor raises an exception if different connection strings are used for separate BamTrackingService instances in the same application domain.  
  
- The interceptor obtains the IC polling interval value from the first BamTrackingService instance that starts.  
  
- The interceptor stops the IC polling thread when last BamTrackingService in application domain is stopped  
  
  For more information on WorkflowRuntime and loading configuration information, see [http://go.microsoft.com/fwlink/?LinkId=83314](http://go.microsoft.com/fwlink/?LinkId=83314).  
  
##### To configure the App.config file for the BAM tracking service  
  
1.  Open the App.config file associated with your application. You can use Notepad.exe or another text editor for this task.  
  
2.  Add the BAM Tracking service by inserting the following configuration information into the App.config file. It should be positioned so that it is a child of the `configuration` element.  
  
    > [!NOTE]
    >  The section element should correspond to the name used by your application code when using the WorkflowRuntime class.  
  
    ```  
    <!-- The element name must match the one expected by WorkflowRuntime in your WF application -->  
    <WorkflowServiceContainer>  
      <Services>  
        <add type="Microsoft.BizTalk.Bam.Interceptors.Workflow.BamTrackingService, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  
       ConnectionString="Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"   
          PollingIntervalSec="5"/>  
        </Services>  
    </WorkflowServiceContainer>  
    ```  
  
3.  Modify the **ConnectionString** attribute to match your environment.  
  
4.  Restart your application.  
  
##### To modify your application to load a custom configuration section  
  
1.  Open your Windows Workflow Foundation project in Visual Studio.  
  
2.  Add a new instance of BamTrackingService with appropriate parameters to the application's instance of WorkflowRuntime:  
  
    ```  
    // !! Replace "WorkflowServiceContainer" with the section name  
    // you used in your App.config file.  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime("WorkflowServiceContainer");  
    ```  
  
3.  Recompile and deploy the modified application.  
  
##### To modify your application to programmatically load the BAM tracking service  
  
1.  Open your Windows Workflow Foundation project in Visual Studio.  
  
2.  Add a new instance of BamTrackingService with appropriate parameters to the application's instance of WorkflowRuntime:  
  
    ```  
    string connectionString = "Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"  
    int pollingInterval = 5;  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime();  
    workflowRuntime.AddService(new BamTrackingService(connectionString, pollingInterval));  
    ```  
  
     You can add or remove parameters based on your specific environment.  
  
3.  Recompile and deploy the modified application.