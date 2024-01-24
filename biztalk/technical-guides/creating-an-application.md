---
description: "Learn more about: Creating an Application"
title: "Creating an Application"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Creating an Application
There are three ways to create a BizTalk application. There are also several options for naming, referencing, and deploying artifacts to applications.

## Creating a BizTalk Application
 The three ways are as follows:

1. Create the BizTalk application by using the New Application command of the BizTalk Server Administration console or the AddApp command of the BTSTask command-line tool. For more information about using these commands, see [How to Create an Application](../core/how-to-create-an-application.md) (https://go.microsoft.com/fwlink/?LinkId=155007).

2. Import an .msi file that was exported from another application. If the application does not already exist in the current BizTalk group, the application, including its artifacts, is automatically created in the current BizTalk group. For more information about importing applications, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md) (https://go.microsoft.com/fwlink/?LinkID=154827).

3. Deploy BizTalk assemblies from Visual Studio into a BizTalk application. If the application specified in the deployment properties for a project in Visual Studio does not exist in the current BizTalk group, it will be automatically created. For more information about deploying an assembly from Visual Studio, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md) (https://go.microsoft.com/fwlink/?LinkID=154719).

   To deploy an application using an .msi file, the destination application does not need to exist, but will be automatically created. However, to import bindings from one application to another, the destination application must already exist. If not, you need to create it by performing one of the procedures listed above.

   For more information about the specific steps required to create an application, see [How to Create an Application](../core/how-to-create-an-application.md) (https://go.microsoft.com/fwlink/?LinkId=155007).

## Application Options
 Before creating a new application, you should do the following:

-   Determine a name that is unique within the BizTalk group for the application.

-   Add a reference from the new application to any application containing artifacts that you want to reuse in the new application. For more information about dependencies between applications, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md) (https://go.microsoft.com/fwlink/?LinkId=155008).

-   Determine whether you want to deploy some artifacts into separate applications, for example, shared artifacts that should be deployed into their own separate application.