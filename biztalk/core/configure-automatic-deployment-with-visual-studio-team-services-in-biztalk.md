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

Using Visual Studio Team Services, you can automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications to different BizTalk environments. 

Typically, there are two roles involved:

- BizTalk developer creates the application, and builds it locally. Then, checks the application into Git or Team Foundation Version Control.
- VSTS admin creates the build and release definitions, and deploys to the BizTalk application to different environments (Dev, UAT, Production).

If you’ve never used VSTS, this walkthrough may be challenging. It does require some understanding of git, including cloning, and pushing changes. 

We show you how to setup VSTS with [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], and add your first application to deploy. We recommend you refer to the [VSTS guidance](https://docs.microsoft.com/vsts/user-guide/), as the VSTS UI changes. 

## Before you begin

* Have your Visual Studio Team Services (VSTS) account ready. Don't have one? [Sign up for Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).
* If you already have a VSTS Agent installed on your BizTalk computer, then the existing agent is overwritten with the latest VSTS Agent. You may have to update your [VSTS service to align with the new agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).

## Prerequisites

* Some experience and knowledge with creating and working with definitions in VSTS. If you're brand new to VSTS, these may be good resources: 

  [Visual Studio Team Services overview](https://www.visualstudio.com/docs/overview)  
  [CI/CD for newbies](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)

## Get started
[Step 1: Add Application project & update .json template](feature-pack-add-application-project.md)  

[Step 2: Create the VSTS token & install the build agent](feature-pack-create-vsts-token.md)

[Step 3: Create the build and release definitions](feature-pack-add-build-release-definitions.md)

[Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md)