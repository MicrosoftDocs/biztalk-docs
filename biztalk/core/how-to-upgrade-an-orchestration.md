---
title: "How to Upgrade an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef3f032f-28a1-4d52-9d85-d5748c9e9682
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Upgrade an Orchestration
How to update an orchestration that is running in a production environment when the orchestration handles long-running transactions or is waiting for a response from a solicit-response port.

## Overview
 When an orchestration does not handle long-running transactions, you can update it as described in [Checklist: Update the Artifacts in a BizTalk Application](../core/checklist-update-the-artifacts-in-a-biztalk-application.md). When an orchestration handles long-running transactions, however, you cannot cut over to the updated version of the orchestration immediately. You must allow the original version to finish processing its messages, so that they are not lost. To accomplish this, you deploy the updated orchestration into the same application as the original one. You then stop the original version and start the updated version so that it receives all new messages while the previous version continues to process any in-flight messages. After the original orchestration has finished processing all of its messages, you undeploy it from the BizTalk application in which it was deployed.  
  
 For more information about this scenario, see [Scenario: Updating Application Artifacts](../core/scenario-updating-application-artifacts.md).  
  
> [!IMPORTANT]
>  If more than one orchestration is bound to the same receive port, and each orchestration is started or enlisted, you will introduce duplicate messages into the system.  
  
> [!NOTE]
>  When upgrading to a new orchestration, some orchestration instances can become Suspended (resumable) under high stress because of the race condition between the old orchestration and the new orchestration during the upgrade. To manually resume these orchestration instances, see [How to Resume Suspended Orchestration Instances](../core/how-to-resume-suspended-orchestration-instances.md).

## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. Your account also must have Read/Write permission on the local file system, and the global assembly cache. The Administrators account on the local computer has this permission.  

For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx). 
 
## Update an orchestration  
  
1.  Make the necessary changes to the orchestration.  
  
2.  Increment the assembly version number, as follows:  
  
    1.  In Solution Explorer, right-click the BizTalk project, and then click **Properties** to launch the Project Designer for the project.  
  
    2.  Click the **Application** tab if it is not already active, and then click **Assembly Information**.  
  
    3.  In the right pane, increase the assembly version number. You should increase only the major or minor version number. The major version number is the first digit in the sequence (**0**.0.0.0); the minor version number is the second digit in the sequence (0.**0**.0.0). BizTalk Server will not recognize a version number change that is later in the sequence, such as 0.0.**0**.0 or 0.0.0.**0**.  
  
    4.  Click **OK** to close the **Assembly Information** dialog box.  
  
    5.  Save the project.  
  
3.  Deploy the assembly from Visual Studio into a BizTalk application. For instructions, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md). Make sure you select the deployment option to install the assembly in the GAC.  
  
4.  Test the assembly containing the orchestration.  
  
5.  Export the assembly from the application in your test environment into an .msi file, as described in [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
    > [!NOTE]
    >  You can use the following steps for testing the assembly as well as deploying it into your production environment. For more information about application deployment tasks in development, test, staging, and production, see [Application Deployment Tasks](../core/application-deployment-tasks.md).  
  
6.  Import the .msi file into the BizTalk application in your production environment that contains the orchestration that you want to update, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).  
  
7.  Bind the updated orchestration using the same bindings as the original orchestration, as described in [How to Configure Bindings for an Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).  
  
8.  Unenlist the original orchestration, and then start the updated orchestration. To avoid any dropped messages, you should do this programmatically, as described in [Deploying and Starting a New Version of an Orchestration Programmatically](../core/deploying-and-starting-a-new-version-of-an-orchestration-programmatically.md). Alternatively, you can perform these steps manually, as described in [How to Unenlist an Orchestration](../core/how-to-unenlist-an-orchestration.md), [How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md), and [How to Start an Orchestration](../core/how-to-start-an-orchestration.md).  
  
9. Monitor the system for instances of the original orchestration version using the Group Hub page query view, as described in [How to View Instance Information for an Orchestration](../core/how-to-view-instance-information-for-an-orchestration.md).  
  
10. When all of its active, dehydrated, and suspended instances are complete, undeploy the original orchestration from the application, as described in [How to Remove an Orchestration from an Application](../core/how-to-remove-an-orchestration-from-an-application.md).  
  
11. Optionally uninstall the original assembly version from the GAC on each computer running the application, as described in [How to Uninstall an Assembly from the GAC](https://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4).  
  
## See Also  
 [Updating BizTalk Applications](../core/updating-biztalk-applications.md)   
 [Managing Orchestrations](../core/managing-orchestrations.md)