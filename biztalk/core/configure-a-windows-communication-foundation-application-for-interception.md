---
title: "How to Configure a Windows Communication Foundation Application for Interception | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37f2ccde-aa79-470a-ac31-57e4168dc54a
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a Windows Communication Foundation Application for Interception
You must install the BAM interceptor software and configure your application to use the BAM [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] interceptor service before you can begin collecting BAM activity data. It is assumed that you have successfully installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and its dependencies and have created at least one BizTalk group.  

## Installing the BAM-Eventing Software  
 Before you can configure your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application to use the BAM interceptor for [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], you must install the BAM-Eventing software by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Setup program. For more information about installing the BAM-Eventing software and registering the performance counters, see [Installing the BAM-Eventing Software](../core/installing-the-bam-eventing-software.md).  

## Configuring a WCF Application for Tracking  
 Four tasks must be completed before your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application can begin writing BAM event information:  

- An observation model must be created by using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM tools and then deployed by using the BAM Manager command line tool (bm.exe).  

- An interceptor configuration file must be created and deployed by using the BAM Manager command line tool (bm.exe).  

- The user running the host application must be a member of the appropriate BAM activity event writer (bam_\<activity\>_EventWriter) SQL Server roles to enable the application to read the interceptor configuration information and write to the BAM activities.  

- The App.config file for the server and client application must be modified to load the BAM tracking service. After the App.config file has been modified, the application must be restarted.  

  Only after these tasks have been successfully completed will events begin appearing in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM database.  

### Deploying an Observation Model  
 You must have an observation model deployed before you can deploy an interceptor configuration file or capture BAM activities in your application.  

##### To deploy an observation model by using bm.exe  

1. Click **Start** and then click **Run** to open the Windows command prompt.  

2. Type **cmd** in the **Open** field, and then click **OK**.  

3. Use the change directory command to move to the directory containing the observation model to deploy. For example, **cd c:\businessprocess\Orders**.  

4. Deploy the observation model using bm.exe:  

    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm.exe deploy-all -Definitionfile:\<*definitionfile.xml*\>  

    Make sure you replace \<*definitionfile.xml*\> with the name of the observation model file you want to deploy. For more options see [Interceptor Management Commands](../core/interceptor-management-commands.md).  

   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  

5. Type **Exit** and then press ENTER to close the command prompt.  

### Deploying an Interceptor Configuration File  
 You must deploy an interceptor configuration file before your application will be able to capture BAM activities.  

##### To deploy an interceptor configuration file by using bm.exe  

1. Click **Start** and then click **Run** to open the Windows command prompt.  

2. Type **cmd** in the **Open** field, and then click **OK**.  

3. Use the change directory command to move to the directory containing the interceptor configuration file to deploy. For example, **cd c:\businessprocess\Orders**.  

4. Deploy the interceptor configuration file by using bm.exe:  

    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm.exe deploy-interceptor -Filename:\<*icfile.xml*\>  

    Make sure you replace \<*icfile.xml*\> with the name of the interceptor configuration file you want to deploy.  

   > [!NOTE]
   >  You can use the **-Force:True** flag to override existing event sources with the same name(s) as those in your interceptor configuration file. If you do so, make sure you back up the existing configuration by using the **get-interceptor** command. Using the -Force:True flag could delete any interceptor configurations that reference the event sources being overwritten.  

   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  

5. Type **Exit** and then press ENTER to close the command prompt.  

   If you have already deployed your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application, the new configuration will not be loaded until the next polling interval. However, if you configure your application and restart it, the configuration will be picked up immediately.  

### Adding the User to the Appropriate BAM Activity Role  
 The BAM Interceptor Framework uses per-activity SQL Server roles to control access to activities and configuration information. You must add the user account running your WCF application to the appropriate BAM activity role(s) in the BAMPrimaryImport database.  

### Configuring the Windows Communication Foundation Application to Load the BAM Tracking Service  
 You configure your application to load the BAM tracking service by adding a few lines to the App.config file for your server or client application.  

 To enable BAM tracking in your [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] server or client application, you will need to modify the App.config configuration file to include an additional endpoint behavior and behavior extension and add a behavior configuration attribute. The formats of the service and client templates are similar.  

 When configuring the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] application, note the following. If there is more than one BAM endpoint behaviors defined in the App.config for the same application, that is, the same client or service, BAM will take the following actions.  

-   If the connection strings differ, BAM will raise and exception.  

-   If only the polling interval differs, BAM will select one and move on. It is not possible at design time to determine which one will be selected.  

> [!NOTE]
>  If the connection strings are the same, meaning that they reference the same computer, BAM processing will proceed normally.  

 The following sample App.config template is configured for a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] server application. It defines an endpoint that uses a custom behavior "bamEndpointBehavior" that is configured to use the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] interceptor.  

```  
<system.serviceModel>  
  <services>  
    <service name="Service.CreditCardAuthorization">  
      <!-- The endpoint will use the "bamEndpointBehavior" -->   
      <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
    </service>  
  </services>  
  <bindings>  
    <wsDualHttpBinding>  
      <binding name="wsDualHttpBinding_ICreditCardAuthorization" transactionFlow="true" />  
    </wsDualHttpBinding>  
  </bindings>  
  <behaviors>  
    <endpointBehaviors>  
      <!-- Define a new behavior named "bamEndpointBehavior" -->  
      <behavior name="bamEndpointBehavior">  
        <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <extensions>  
    <behaviorExtensions>  
      <!-- Define a new enpoint behavior extension using WCF interceptor -->  
      <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </behaviorExtensions>  
  </extensions>  
</system.serviceModel>  
```  

 You will need to make small changes to this template before using it in your own App.config file.  

##### To use this template in your WCF service App.config file  

1. Open the App.config file associated with your application. You can use Notepad.exe or another text editor for this task.  

2. Add the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] BamEndpointBehavior behavior extension to the `extensions` element by using the following XML:  

   ```  
   <behaviorExtensions>  
     <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
   </behaviorExtensions>  
   ```  

   > [!NOTE]
   >  The behavior extension is named "BamEndpointBehaviorExtension" and can be changed as needed to suit your environment.  

3. Add a new endpoint behavior that uses the new behavior extension to the `behaviors` element by using the following XML. The behavior extension provides a connection string and polling interval in seconds.  

   ```  
   <endpointBehaviors>  
     <behavior name="bamEndpointBehavior">  
       <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
     </behavior>  
   </endpointBehaviors>  
   ```  

    Replace the Data Source with the name of the computer hosting the BamPrimaryImport database in your environment. Change the polling interval to suit your requirements; a higher number means that the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] interceptor will take longer to detect configuration changes. If you changed the name of the behavior extension, use it to replace "BamEndpointBehaviorExtension".  

   > [!NOTE]
   >  The behavior name is "bamEndpointBehavior" and can be changed to suit your environment.  

   > [!NOTE]
   >  Avoid using a cleartext username/password combination when specifying `ConnectionString`. Doing so may compromise your database server.  

   > [!NOTE]
   >  You must specify an `PollingIntervalSec` greater than or equal to 5 (seconds). If you specify a lower value or omit the `PollingIntervalSec` element, an error will be raised and interception will not be configured.  

4. Add the `behaviorConfiguration` attribute to the endpoint you will be tracking and provide the name of the new behavior:  

   ```  
   <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
   ```  

   > [!NOTE]
   >  If you used a different behavior name, supply it instead.  

    You can apply the behavior configuration to multiple endpoints.  

5. Save the modified App.config file and restart your application.
