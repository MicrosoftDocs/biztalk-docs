---
title: "Configure automatic deployment with Visual Studio Team Services | Microsoft Docs"
description: Install BizTalk Feature Pack to use application lifecycle management with VSTS to deploy your applications to different BizTalk environments
ms.custom: ""
ms.date: "11/20/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57f769bb-5105-43e2-9096-ed54cdf82b90
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: "anneta"
---
# Configure automatic deployment with Visual Studio Team Services in BizTalk Server

## Overview

**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] provides an improved automatic deployment and application lifecycle management (ALM) experience. 

**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, we've improved this feature:

* Within Visual Studio, set the **Application Name** of your BizTalk application
* In addition to using an agent-based deployment, you can also use [deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index) to deploy your BizTalk applications to multiple servers
* In the release task, you can install the BizTalk application, and enter the BizTalk management computer, and the path to the deployment package

Using Visual Studio Team Services, you can automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications to different BizTalk environments. 

Typically, there are two roles involved:

- BizTalk developer creates the application, and builds it locally. Then, checks the application into Git or Team Foundation Version Control.
- VSTS admin creates the build and release definitions, and deploys to the BizTalk application to different environments (Dev, UAT, Production).

If you’ve never used VSTS, this walkthrough may be challenging. It does require some understanding of git, including cloning, and pushing changes. 

We show you how to setup VSTS with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and add your first application to deploy. We recommend you refer to the [VSTS guidance](https://docs.microsoft.com/vsts/user-guide/), as the VSTS UI changes. 

## Before you begin

* Have your Visual Studio Team Services (VSTS) account ready. Don't have one? [Sign up for Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).
* If you already have a VSTS Agent installed on your BizTalk computer, then the existing agent is overwritten with the latest VSTS Agent. You may have to update your [VSTS service to align with the new agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).
* With Feature Pack 1, automatic deployment with VSTS is done on one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group. Be sure the computer has Visual Studio and the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] Developer Tools and SDK installed. See the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [hardware and software requirements](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).
* With Feature Pack 2, automatic deployment with VSTS can be done using [deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/howto-deployment-groups). Using deployment groups, you can deploy your applications to multiple BizTalk Servers within the deployment group.

## Prerequisites

* Install [Feature Pack 2](https://aka.ms/bts2016fp2) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* Some experience and knowledge with creating and working with definitions in VSTS. If you're brand new to VSTS, these may be good resources: 

  [Visual Studio Team Services overview](https://www.visualstudio.com/docs/overview)  
  [CI/CD for newbies](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)

## Get started
[Step 1: Add Application project & update .json template](feature-pack-add-application-project.md)  

[Step 2: Create the VSTS token & install the build agent](feature-pack-create-vsts-token.md)

[Step 3: Create the build and release definitions](feature-pack-add-build-release-definitions.md)

[Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md)