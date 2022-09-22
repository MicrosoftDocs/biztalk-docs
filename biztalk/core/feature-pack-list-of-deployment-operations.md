---
title: List of deployment operations
description: In Azure DevOps, create a release definition to deploy the BizTalk Server application
ms.custom: ""
ms.date: "9/20/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
author: MandiOhlinger
ms.author: abkumar
manager: "anneta"
---


# List of deployment operations


## Create new BizTalk Server Appication

:::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-create-operation.PNG" alt-text="Create BizTalk Server application as a deployment task for Azure DevOps in Visual Studio.":::


 Deploys a new application. If the application already exists, it uninstalls the current applications (full stop), and installs the new application.

### Parameters 

**Deployment package:**  Path of the zip file to your application project. This is a mandatory parameter.

### Advanced Options


:::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-create-advanced.PNG" alt-text="Advanced options in Create BizTalk Server application as a deployment task for Azure DevOps in Visual Studio.":::


**Start Application:** Lets the user decide if the application should be started. By default, the application is started once it is deployed. If this option is unchecked, application will not be started.


**Add application references:** This is an optional parameter. Takes a comma-separated list of referenced applications. These references are created after the deployment of application is completed.



## Update new BizTalk Server Appication

:::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-update-operation.PNG" alt-text="Update BizTalk Server application as a deployment task for Azure DevOps in Visual Studio.":::


Deploys a new application. If the application already exists, it uninstalls the current applications (full stop), and installs the new application.

### Parameters 

**Deployment package:**  Path of the zip file to your application project. This is a mandatory parameter.


### Advanced Options

:::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-update-advanced.PNG" alt-text="Advanced options for update BizTalk Server application as a deployment task for Azure DevOps in Visual Studio.":::


**Stop referenced application(s):** 
Lets the user decide if application(s) that refer to the application being updated should be stopped during the update. By default, referenced applications are stopped during the deployment and started at the end of it. If this option is unchecked, the referenced application(s) will not be stopped during update operation.


## Install BizTalk Server Appication

:::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-install-operation.PNG" alt-text="Update BizTalk Server application as a deployment task for Azure DevOps in Visual Studio."::: 

Installs the application MSI on the server. Refer to [Install the applications](../core/how-to-install-a-biztalk-application.md) for details.

Please note that the application must already be deployed to the BizTalk Server Group. If it’s a new application, or is being updated, please choose either Create or Update operation as applicable

### Parameters 

**Application Name:** Name of the application that needs to be installed.

    Note: Deployment Package Path paramter should not be used. This parameter has been kept to maintain backward compatibility with earlier version(s). Will be removed going forward.
