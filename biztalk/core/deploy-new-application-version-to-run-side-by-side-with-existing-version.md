---
title: "How to Deploy a New Version of an Application to Run Side-by-side with an Existing Version | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1677c6a5-2c4c-4d70-ab83-f7e0bb3aaf6e
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Deploy a New Version of an Application to Run Side-by-side with an Existing Version
How to deploy a new version of an application that will run side-by-side with an existing version. 

## Overview
You might want to do this to roll out a major application upgrade incrementally, for example making it available to a subset of business partners initially, rather than to all partners at once. Using this approach allows you to continue running the existing application to service the users who are not yet using the new version until you are ready to completely cut over to the new version. For background information on this scenario, see [Scenario: Deploying Two Versions of an Application](../core/scenario-deploying-two-versions-of-an-application.md).  
  
 You do not create application versions in the same manner that you create assembly versions, by incrementing the version number. Instead, you create a new application that has a different name than the original application, and populate it with the new versions of the application artifacts.  
  
 Because many types of artifacts, such as assemblies, can exist in only one application in a BizTalk group, you must increment the version number of any assemblies that already exist in the group before you can deploy them into the new application. For more information, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).  

## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. Your account also must have Read/Write permission on the local file system, and the global assembly cache. The Administrators account on the local computer has this permission.  

For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx). 
  
## Deploy a new version of an application  
  
1. In Visual Studio, make any necessary changes to the assemblies that you want to deploy into the new version of the application  
  
2. Increment the version number of each assembly, as follows:  
  
   1.  In Solution Explorer, right-click the BizTalk project, and then click **Properties** to launch Project Designer for the project.  
  
   2.  Click the **Application** tab if it is not active, and then click **Assembly Information** button.  
  
   3.  Increase the assembly version number, and then click **OK**.  
  
   4.  Save the project.  
  
   > [!NOTE]
   >  Use the Pipeline Designer Object Model to avoid schema collisions when incrementing assembly versions.  
  
3. In deployment properties for each project in the solution, do the following:  
  
   - Change the application name to the name you want to use for the new application.  
  
   - Ensure that the option to install the assemblies in the global assembly cache (GAC) is selected.  
  
     For instructions, see [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). When you deploy the solution, the assemblies will be deployed into the new application and installed in the GAC.  
  
4. Deploy the solution(s) containing the assemblies. For instructions, see [How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).  
  
5. Create a new receive port and any needed receive locations specifying the new URL(s) to which you want partners to send messages. For instructions, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md). Also see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  
  
6. Create the appropriate send ports as necessary, as described in [How to Create a Send Port](../core/how-to-create-a-send-port2.md).  
  
7. Bind the new application to the newly created receive and send ports, as described in [How to Configure an Application](../core/how-to-configure-an-application.md).  
  
8. Export the application into an .msi file from your test environment, as described in [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
   > [!NOTE]
   >  You can use the following steps for testing the application as well as deploying it into your production environment. For more information about application deployment tasks in development, test, staging, and production, see [Application Deployment Tasks](../core/application-deployment-tasks.md).  
  
9. Import the application .msi file into the BizTalk group in your production environment, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md). If the application requires references, you can add them while using the Import MSI Wizard, or later as described in [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).  
  
10. Install the new application on each host instance that will run it, as described in [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md). Verify that each updated assembly has been installed in the GAC on each computer that hosts the assembly. If necessary, install the assemblies in the GAC, as described in [How to Install an Assembly in the GAC](../core/how-to-install-an-assembly-in-the-gac.md).  
  
11. Perform a Full Start of the application, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
12. Notify your partners that they should begin sending messages to the new URLS. Once they do this, the application begins processing messages for the specified partners.  
  
## See Also  
 [Updating BizTalk Applications](../core/updating-biztalk-applications.md)