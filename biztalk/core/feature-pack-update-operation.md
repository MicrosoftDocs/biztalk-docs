---
title: Operation Name : Create new BizTalk application
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


# OperationName: Update new BizTalk application


### Create new BizTalk Server Appication

:::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-update-operation.PNG" alt-text="Update BizTalk Server application as a deployment task for Azure DevOps in Visual Studio.":::


Deploys a new application. If the application already exists, it uninstalls the current applications (full stop), and installs the new application.

### Parameters 

**Deployment package:**  Path of the zip file to your application project. This is a mandatory parameter.


## Advanced Options

:::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-update-advanced.PNG" alt-text="Advanced options for update BizTalk Server application as a deployment task for Azure DevOps in Visual Studio.":::


**Stop referenced application(s):** 
Lets the user decide if application(s) that refer to the application being updated should be stopped during the update. By default, referenced applications are stopped during the deployment and started at the end of it. This option can be unchecked if referenced application(s) need not stop.