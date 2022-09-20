---
title: Operation Name : Install BizTalk application
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


# OperationName: Install BizTalk application

### Install BizTalk Server Appication

:::image type="content" source="./media/feature-pack-add-build-release-definitions/azure-devops-install-operation.PNG" alt-text="Update BizTalk Server application as a deployment task for Azure DevOps in Visual Studio."::: 

Installs the application MSI on the server. Please note that the application must already be deployed to the BizTalk Server Group. If it’s a new application, or is being updated, please choose either Create or Update operation as applicable

### Parameters 

**Application Name:** Name of the application that needs to be installed.

**Deployment Package Path**: This paramter should not be used 