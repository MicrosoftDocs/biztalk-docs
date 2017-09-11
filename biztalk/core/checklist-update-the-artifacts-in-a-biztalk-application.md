---
title: "Checklist: Update the Artifacts in a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, redeploying"
  - "updating, applications"
  - "redeploying"
  - "checklists, applications"
  - "updating, checklists"
  - "updating"
  - "applications, updating"
  - "applications, redeploying"
  - "applications, checklists"
  - "checklists, redeploying"
ms.assetid: 07ea4a2b-4ada-4d04-9eec-604b63b77415
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Update the Artifacts in a BizTalk Application
Follow the steps in this checklist if you want to change or update one or more artifacts in an application that has already been deployed, and then redeploy the application.  
  
|Step|Reference|  
|----------|---------------|  
|Review the important considerations for updating artifacts in an application.|[Important Considerations for Updating Applications](../core/important-considerations-for-updating-applications.md)|  
|Ensure that you have appropriate permissions to perform the deployment.|[Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)|  
|Make any necessary changes to your assemblies in Visual Studio. If you are updating an assembly that is running in a production environment, you should always increment the assembly version number. For background information, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md). Then deploy the assemblies from Visual Studio into a BizTalk application in the development environment.|[How to Deploy a BizTalk Assembly from Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)|  
|Test any new or changed artifacts, ensuring that any artifacts that may depend on the new or changed artifact are also tested. While testing, be sure to consider dependencies that may exist between this application and other applications.|[Testing Tasks for BizTalk Application Deployment](../core/testing-tasks-for-biztalk-application-deployment.md)|  
|Add, remove, or reconfigure artifacts in the application as necessary.|[How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md), [How to Remove an Artifact from an Application](../core/how-to-remove-an-artifact-from-an-application.md), [Managing Artifacts](../core/managing-artifacts.md)|  
|Export the application containing the new or changed artifacts into an .msi file. You may either export all of the artifacts in the application or only the artifacts you want to add or update. Be aware that file artifacts can be overwritten. If you export a file artifact, make sure that it is the version that you want to use in the application.|[Exporting BizTalk Applications, Bindings, and Policies](../core/exporting-biztalk-applications-bindings-and-policies.md)|  
|If the update will interfere with the application as it runs, stop the application that you want to update. If you are updating an assembly with a new version, you do not need to restart the application. **Note:**  Although it is not required to stop an application in order to update an artifact or install the application, we recommend that you always stop an application when you update an artifact.|[How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md)|  
|Import the changed or updated artifacts from the .msi file into the application that you want to update. Be sure to specify the option to overwrite existing artifacts.|[How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md)|  
|Install the updated application or artifacts from the .msi file onto all of the computers that run the application as well as any computers running applications that depend on this application. If you are updating a BizTalk assembly, verify that the new version of the assembly is installed in the global assembly cache (GAC) on each computer that is to run the assembly. If not, install the assembly in each GAC.|[How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md), [How to Install an Assembly in the GAC](../core/how-to-install-an-assembly-in-the-gac.md)|  
|Start the application.|[How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md)|  
|After importing an assembly that contains an orchestration, if the application to which you are importing it already contains an assembly that has the same name, public key token, and version, stop and start the host instances of the host to which the orchestration is bound. This ensures that the new version of the assembly is used by BizTalk Server.|[How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md), [How to Start a Host Instance](../core/how-to-start-a-host-instance.md)|  
  
## See Also  
 [BizTalk Application Deployment and Management Checklists](../core/biztalk-application-deployment-and-management-checklists.md)   
 [Updating BizTalk Applications](../core/updating-biztalk-applications.md)