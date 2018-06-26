---
title: "Best Practices for Deploying an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53852303-d368-4f9e-b4e2-f5918f65000b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Deploying an Application
This topic lists best practices that you should follow in deploying BizTalk applications.  

## Deploying a BizTalk Application  
 **Document application deployment procedures**  

- Make sure that all the procedures used in application deployment are documented in depth, so you have a record of how the deployment was performed and will know how to deploy further or undeploy. Anything that is not scripted should be documented with detailed steps. This should include documenting any changes to external systems and deployment of third-party components.  

  **Script application deployment**  

- Script as many application deployment steps as possible. Scripting reduces the risk of human error during the deployment process.  

## Creating a BizTalk Application  
 **Script the creation of BizTalk application and .msi files**  

-   BtsTask.exe can be used to script the creation of BizTalk applications. If the creation of the applications is scripted, then the packages can be automatically built using an automated process on a build server. For more information about scripting the creation of applications, see [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md).

## Deploying a BizTalk Assembly  
 **Never deploy an assembly from Visual Studio on a production computer**  

-   During the development process, a developer must often redeploy assemblies from Visual Studio. To enable the redeployment, Visual Studio may undeploy, unbind, stop, and unenlist artifacts included in the assemblies. Although this is necessary and appropriate in the development environment, it can cause unexpected and undesired consequences in a production environment. For this reason, as well as to prevent anyone from deploying an assembly from Visual Studio on a production computer, we recommend that you never install Visual Studio on a production computer.  

-   In addition, never refer to a production database from a computer running Visual Studio.  

## Adding Artifacts to a BizTalk Application  
 **Group related artifacts together in a single application**  

- As much as possible, place related artifacts in the same BizTalk application. This allows you to manage and deploy the artifacts as a single entity, making management easier. You can group artifacts that support the same business process or artifacts that perform similar functions into a single application.  

  **Deploy shared artifacts in a separate application**  

- If artifacts are going to be shared by two or more applications, deploy the shared artifacts into a separate application. For example, if two applications share a schema, place the schema in a separate application. We recommend this because only one artifact in a BizTalk group can have a single locally unique identifier (LUID). A LUID consists of the artifact name and optionally other attributes. If you include an artifact in one application, and then create a reference to it from another application, the referring application may not function correctly when you stop the application containing the artifact.  

   This best practice applies to all artifact types except for files, such as Readme files and scripts, which are added to the application as a File type of artifact. This is because more than one file artifact with the same name can be deployed in a BizTalk group. Therefore, you can use a file having the same name in two or more applications. In this case, stopping one application will not impact the other application. For more information about adding file artifacts, see [How to Add a File to an Application](../core/how-to-add-a-file-to-an-application.md).  

  **Deploy a shared Web site in a separate application**  

- If a Web site will be shared by more than one business solution, deploy the Web site in a separate application. This is because when you uninstall a BizTalk application, the virtual directory of any Web site that is part of the application is removed, even if the Web site is running. If the Web site is shared with another business solution, the other business solution will no longer function correctly as a result.  

  **Deploy shared policies in a separate application**  

- If a policy is used by two or more applications, you should deploy it in a separate application rather than creating a reference from one application to another. This is because when you stop an application, its policies are undeployed. If you stop an application that includes a policy used by another application, the policy will no longer function in either application.  

  **Deploy shared certificates in a separate application**  

- If a certificate is used by a send port or receive location in two or more applications, you should deploy the certificate in a separate application, and then reference this application from the applications that need to use the certificate. This is because only one artifact in a BizTalk group can have a single LUID, so you will not be able to import the same certificate in two different applications. If you attempt to import two applications that each use the same certificate, the first import will succeed, and the second will not. In this case, using the Overwrite import option does not correct the problem, as the existing certificate that you want to overwrite is contained in another application.  

## Exporting and Importing a BizTalk Application  
 **When deploying large .msi files, you may need to increase the default transaction timeout of the COM+ components used by BizTalk Server to deploy applications**  

- If you attempt to deploy an .msi file that is very large (more than 100 MB), then the application may not be deployed within the default transaction time-out of the COM+ components that are used by BizTalk Server during application deployment. If the transactions associated with these COM+ components time out before the deployment is completed, then the deployment will fail. If you are deploying very large .msi files, then consider taking one of these approaches to mitigate this problem:  

- Deploy several smaller .msi files instead of one large .msi file.  

  -   Increase the default transaction timeout of 3,000 seconds associated with the Microsoft.BizTalk.ApplicationDeployment.Group and the Microsoft.BizTalk.Deployment.DeployerComponent components in the Component Services management interface. These components belong to the Microsoft.BizTalk.ApplicationDeployment.Engine and Microsoft.Biztalk.Deployment COM+ applications, respectively. For more information, see Microsoft Knowledge Base article 287499, [How to Change the Transaction Time-Out Value for MTS or COM+](https://support.microsoft.com/help/287499/how-to-change-the-transaction-time-out-value-for-mts-or-com).  

  **Prevent bindings from being overwritten**  

- If you do not want the bindings in the application you are exporting to overwrite the bindings in an application into which you are importing the .msi file, then you should not select the binding file as a resource to export during the export operation.  

  **Ensure that the .msi file is secure**  

- An .msi file may contain sensitive data. Be sure to take steps to help ensure that the file is secure. For more information about .msi file security, see [Security and Windows Installer](../core/security-and-windows-installer.md).  

  **Ensure that the binding file is secure**  

- A binding file may contain sensitive data. Be sure to take steps to help ensure that the file is secure.  

  **Schedule exports when no one is making changes to an artifact**  

- Schedule export operations during hours when users are not likely to be making changes to artifacts. This can be important because if a user is modifying a database-based artifact, virtual directory, certificate, or policy while an export operation is in progress, the changes will not be reflected in the exported .msi file.  

## Importing a BizTalk Application  
 **Script the importing of .msi files**  

- BtsTask.exe can be used to script the importing of existing BizTalk .msi files. For more information about scripting .msi file importing, see [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md). 

  > [!NOTE]  
  >  The white paper also applies to BizTalk Server.  

- You can add scripts to run as pre-processing or post-processing scripts. However, you will have to include logic in your scripts to check environment variables to determine which context the script is executing in (an import, installation, or uninstallation) and process accordingly. For more information about using pre- and post-processing scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md). 

  **Verify the existence of referenced artifacts**  

- When an application that you are importing has a reference to another application, BizTalk Server verifies that the referenced application exists. However, it does not verify that the artifacts on which your application has dependencies are included in the referenced application. When you import an application that has dependencies to artifacts in another application, we recommend that you verify that the referenced application contains the required artifact or artifacts.  

  **Importing from an .msi file precludes storing changed assemblies in the global assembly cache**  

- To update the artifacts in an application, import the changed or updated artifacts from an .msi file into the application. If you do not use an .msi file to import the artifacts, you will need to update all servers in the group by storing the changed assemblies in the global assembly cache.  

  **Host processing groups to update a subset of total servers**  

- When updating artifacts in an application, you must normally update all servers in a BizTalk group. However, if you use host processing groups, you only need to update a subset of the total servers in the group.  

  **If an import operation times out, split the application into additional .msi files**  

- An import operation will time out if it exceeds 3,600 seconds in duration. If you are attempting to import an .msi file and the operation times out, you should divide the contents of the application into more than one .msi file by re-exporting the application and selecting a subset of artifacts to export. For more information about exporting an application into an .msi file, see [Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).
