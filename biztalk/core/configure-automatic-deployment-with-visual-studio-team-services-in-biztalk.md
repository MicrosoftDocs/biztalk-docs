---
title: "Configure automatic deployment with Visual Studio Team Services"
description: Install BizTalk Feature Pack to use application lifecycle management with Azure DevOps to deploy your applications to different BizTalk environments
ms.custom: "biztalk-2020"
ms.date: "09/20/2022"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configure automatic deployment with Visual Studio Team Services in BizTalk Server

## Overview

Using Azure DevOps, you can automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications to different BizTalk environments. 

Typically, there are two roles involved:

- BizTalk developer creates the application, and builds it locally. Then, checks the application into Git or Team Foundation Version Control.
- Azure DevOps admin creates the build and release definitions, and deploys to the BizTalk application to different environments (Dev, UAT, Production).

If you’ve never used Azure DevOps, this walkthrough may be challenging. It does require some understanding of git, including cloning, and pushing changes. 

We show you how to setup Azure DevOps with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and add your first application to deploy. We recommend you refer to the [VSTS guidance](/vsts/user-guide/), as the Azure DevOps UI changes. 

## Before you begin

* Have Azure DevOps account ready. Don't have one? [Sign up for Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).
* If you already have an Azure DevOps Agent installed on your BizTalk computer, then the existing agent is overwritten with the latest Azure DevOps Agent. You may have to update your [VSTS service to align with the new agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).

## Prerequisites

* Some experience and knowledge with creating and working with definitions in Azure DevOps. If you're brand new to Azure DevOps, these may be good resources: 

  [Visual Studio Team Services overview](https://www.visualstudio.com/docs/overview)  
  [CI/CD for newbies](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)

## Get started
[Step 1: Add Application project & update .json template](feature-pack-add-application-project.md)  

[Step 2: Create the Azure DevOps token & install the build agent](feature-pack-create-vsts-token.md)

[Step 3: Create the build definition](feature-pack-add-build-release-definitions.md)

[Step 4: Create the release definition](azure-devops-add-release-definition.md)

[Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md)
