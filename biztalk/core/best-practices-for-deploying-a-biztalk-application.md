---
description: "Learn more about: Best Practices for Deploying a BizTalk Application"
title: "Best Practices for Deploying a BizTalk Application"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: best-practice
---
# Best Practices for Deploying a BizTalk Application
This topic describes best practices for deploying a BizTalk application.

## Group related artifacts together in a single application
 As much as possible, place related artifacts in the same BizTalk application. This allows you to manage and deploy the artifacts as a single entity, making management easier. You can group artifacts that support the same business process or artifacts that perform similar functions into a single application.

## Deploy shared artifacts in a separate application
 If artifacts are going to be shared by two or more applications, deploy the shared artifacts into a separate application. For example, if two applications share a schema, place the schema in a separate application. This is because only one artifact having the same locally unique identifier (LUID) -- which consists of the artifact name and optionally other attributes -- can exist in a BizTalk group. If you include an artifact in one application, and then create a reference to it from another application, you may encounter problems such as the referring application not functioning correctly when you stop the application containing the artifact.

 This best practice applies to all artifact types except for files, such as Readme files and scripts, which are added to the application as a File type of artifact. This is because more than one file artifact having the same name can be deployed in a BizTalk group. Therefore, you can use a file having the same name in two or more applications. Stopping one application will not impact the other application. For more information about adding File artifacts, see [How to Add a File to an Application](../core/how-to-add-a-file-to-an-application.md).

 For best practices on sharing specific artifact types, see "Deploy a shared Web site in a separate application," "Deploy shared policies in a separate application," and "Deploy shared certificates in a separate application" in this section.

## Deploy a shared Web site in a separate application
 If a Web site will be shared by more than one business solution, deploy the Web site in a separate application. This is because when you uninstall a BizTalk application, the virtual directory of any Web site that is part of the application is removed, even if the Web site is running. If the Web site is shared with another business solution, the other business solution will no longer function correctly as a result.

## Deploy shared policies in a separate application
 If a policy is used by two or more applications, you should deploy it in a separate application rather than creating a reference from one application to another. This is because when you stop an application, its policies are undeployed. If you stop an application that includes a policy used by another application, the policy will no longer function in either application.

## Deploy shared certificates in a separate application
 If a certificate is used by a send port or receive location in two or more applications, you should deploy the certificate in a separate application, and then reference this application from the applications that need to use the certificate. This is because only one artifact having a particular LUID can exist in the BizTalk group, so you will not be able to import the same certificate in two different applications. If you attempt to import two applications that each use the same certificate, the first import will succeed, and the second will not. In this case, using the Overwrite import option does not correct the problem, as the existing certificate that you want to overwrite is contained in another application.

## Never deploy an assembly from Visual Studio on a production computer
 During the development process, the developer often must redeploy assemblies from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To enable the redeployment, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] may undeploy, unbind, stop, and unenlist artifacts included in the assemblies. Although this is necessary and appropriate in the development environment, it can cause unexpected and undesired consequences in a production environment. For this reason, as well as to avoid the possibility of anyone's attempting to deploy an assembly from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on a production computer, we recommend that you never install [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] on a production computer.

 In addition, never refer to a production database from a computer running [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].

## When deploying large MSI files, you may need to increase the default transaction timeout of the COM+ components used by BizTalk to deploy applications
 If the MSI file being deployed is very large (over 100 MB) then the application may not be deployed within the default transaction timeout of the COM+ components that are used by BizTalk during application deployment. If the transactions associated with these COM+ components time out before the deployment is completed then the deployment will fail. If you are deploying very large MSI files then consider taking one of these approaches to mitigate this problem:

1.  Deploy several smaller MSI files instead of one large MSI file.

2.  Increase the default transaction timeout of 3000 seconds associated with the **Microsoft.BizTalk.ApplicationDeployment.Group** and the **Microsoft.BizTalk.Deployment.DeployerComponent** components in the **Component Services** management interface. These components belong to the **Microsoft.BizTalk.ApplicationDeployment.Engine** and **Microsoft.Biztalk.Deployment** COM+ applications respectively. For more information about how to change the transaction timeout value, go to [Setting the Transaction Time-Out](/windows/win32/cossdk/setting-the-transaction-time-out).

## See Also
 [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md)
