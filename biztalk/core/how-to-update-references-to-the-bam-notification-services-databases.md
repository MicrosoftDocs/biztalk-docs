---
title: "How to Update References to the BAM Notification Services Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Notification Services Application database [BAM], restoring"
  - "Notification Services Application database [BAM], updating references"
  - "restoring, BAM"
  - "NS$instance_name service Notification Services Application database [BAM], NS$instance_name service"
  - "restoring [BAM], updating references"
  - "BAM, restoring"
  - "restoring [BAM], Notification Services Application database"
  - "restoring [BAM], NS$instance_name service"
ms.assetid: b007fdc2-2e74-4eef-b4c3-43689e9f2180
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Update References to the BAM Notification Services Databases
After you perform the steps necessary to restore the Business Activity Monitoring (BAM) Notification Services databases to the destination system, you must re-register the Notification Service on all computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group that are running Notification Services (NSservice.exe). This enables Notification Services to connect to the databases in their new location.  
  
 Registering an instance of Notification Services creates the NS$instance_name service, creates performance counters on the local server, and adds information to the registry. You must register the instance on the following servers:  
  
- Each server that runs the NS$instance_name service. The service runs the event provider host, generator, and distributor components. For scaled-out configurations, the service runs on multiple servers.  
  
- Each server that runs a subscription management application. If the subscription management application runs on its own server, do not create the NS$instance_name service when registering the instance.  
  
- Each server that runs an independent event provider. If the independent event provider runs on its own server or the database server, do not create the NS$instance_name service when registering the instance.  
  
  If the database server does not also run the Notification Services instance or the client components, do not register the instance on this server.  
  
## Prerequisites  
  
-   You must be logged on as a member of the Administrators group to perform this procedure.  
  
-   The Business Activity Monitoring (BAM) Alert Provider for SQL Notification Services must be installed on the computer where you are restoring the BAM Notification Services databases.  
  
### To update references to the BAM Notification Services databases (SQL Server 2008 R2/SP1)  
  
1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3. Type: **bm.exe get-config –filename:config.xml**  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4. Open the xml file created in step 2 to obtain the list of the computers on which you must re-register Notification Services.  
  
    The computer names are listed in the **\<Property Name\=\>** parameters in the **\<DeploymentUnit Name="Alert"\>** section of the xml file:  
  
   ```  
   -<DeploymentUnit Name="Alert">  
   <Property Name="GeneratorServerName" />  
   <Property Name="ProviderServerName" />  
   <Property Name="DistributorServerName" />  
     </DeploymentUnit>  
   ```  
  
5. On each computer listed in the xml file, stop the NS service and then unregister an instance of Notification Services:  
  
   1.  Click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.  
  
   2.  At the command prompt, type: **net stop NS$BamAlerts**  
  
   3.  Type the following command to unregister the instance:  
  
        **nscontrol unregister  -name BamAlerts**  
  
        Unregistering an instance removes the registry entries, removes the NS$instance_name service (if present), and deletes the performance counters for the service.  
  
6. Re-register the Notification Service:  
  
   1.  Click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.  
  
   2.  At the command prompt, type: **nscontrol register -name BamAlerts -server** *\<ServerName\>***-service -serviceusername "***\<ServiceUserName\>***" -servicepassword "***\<ServicePassword\>***"**  
  
        This enables Notification Services to log on to the correct database (this information is maintained in the registry of the service machine by nscontrol).  
  
       > [!IMPORTANT]
       >  Remember to use the new Notification Services databases server in the **-server** option when re-registering the service. In addition, you should use the same user name for the new Notification Services service as the old one.  
  
7. On the computer that hosts the BAM portal, click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.  
  
8. At the command prompt, type:  
  
    **net stop NS$BamAlerts**  
  
9. At the command prompt, type:  
  
     **nscontrol unregister  -name BamAlerts**  
  
10. At the command prompt, type:  
  
     **nscontrol register  -name**  *\<BamAlerts\>*  **-server** *\<NotificationServicesDatabaseServer\>*  
  
11. At the command prompt, type: **net start NS$BamAlerts**.  
  
12. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
13. At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
14. At the command prompt, type:  
  
     **bm.exe update-config –FileName:config.xml**  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md)