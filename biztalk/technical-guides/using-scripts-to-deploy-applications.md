---
description: "Learn more about: Using Scripts to Deploy Applications"
title: "Using Scripts to Deploy Applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e683c5f-7576-4382-9952-d577cd00186c
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Scripts to Deploy Applications
You should use scripts to deploy BizTalk applications where possible. Scripting reduces the risk of human error during the deployment process. You should also document your deployment procedures in depth. You should document anything that you do not script with very detailed steps. This includes documenting any changes to external systems and to deployment of non-Microsoft components.

## Using BTSTask
 You can use BTSTask.exe to script the creation of BizTalk applications, as well as to import existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi packages. If the creation of the applications is scripted, then the packages can be automatically built using an automated process on a build server.

 See the following topics for more information about scripting BizTalk application deployments:

-   [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md) (https://go.microsoft.com/fwlink/?LinkId=154210)

-   [Understanding BizTalk Server Application Deployment](https://go.microsoft.com/fwlink/?LinkId=101599) (https://go.microsoft.com/fwlink/?LinkId=101599)

    > [!NOTE]
    >  This latter article also applies to BizTalk Server.

## See Also
 [Checklist: Configuring BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)