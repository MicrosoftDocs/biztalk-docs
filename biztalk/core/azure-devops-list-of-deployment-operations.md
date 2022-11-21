---
title: List of deployment operations
description: List of operations available in Azure DevOps task to deploy the BizTalk Server application
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

## Create new BizTalk Server Application

Deploys a new application. If the application already exists, it uninstalls the current applications (full stop), and installs the new application. If continuous integration is enabled, it automatically redeploys the application when it is updated in the repository.

### Parameters

- **Deployment package path**: Mandatory. Path of the BizTalk Application package in zip format, which can be selected from Linked artifacts.

#### Advanced Options

- **Start application**: Specifies whether the application should be started after it is deployed. It is checked by default. If this option is unchecked, application will not be started.

- **Add application references**: Optional. Comma-separated list of referenced applications.


## Update an existing BizTalk Server Application

Appends changes, such as schemas, to an already running application. It does not require a full redeploy of the application.

### Parameters

- **Deployment package path**: Mandatory. Path of the BizTalk Application package in zip format, which can be selected from Linked artifacts.

#### Advanced Options

- **Stop referenced application(s)**: Lets the user decide if application(s) that refer to the application being updated should be stopped during the update. By default, referenced applications are stopped before the deployment and started after the deployment is complete . If this option is unchecked, the referenced application(s) will not be stopped during update operation.


## Install BizTalk Server Application

Installs the application MSI on the server. Refer to [Install the applications](../core/how-to-install-a-biztalk-application.md) for details.

> [!NOTE]
> The application must already be deployed to the BizTalk Server Group. If this is a new application, or is being updated, please choose either **Create** or **Update** operation as applicable.

### Parameters

- **Application name**: Recommended. Name of the application that needs to be installed.

> [!NOTE]
> **Deployment package path** parameter is deprecated for the Install operation, and should not be used. Please use **Application name** parameter instead. If you continue to use the Deployment pacakge path parameter, you will start seeing warnings in your release pipeline. This parameter has been retained to maintain backward compatibility with earlier version(s) of the task, and will be removed in a future release.


## See also

[Configure automatic deployment with Visual Studio Team Services](configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  
