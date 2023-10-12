---
description: "Learn more about: Using Scripts to Deploy Applications"
title: "Using Scripts to Deploy Applications"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Using Scripts to Deploy Applications
You should use scripts to deploy BizTalk applications where possible. Scripting reduces the risk of human error during the deployment process. You should also document your deployment procedures in depth. You should document anything that you do not script with very detailed steps. This includes documenting any changes to external systems and to deployment of non-Microsoft components.

## Using BTSTask
 You can use BTSTask.exe to script the creation of BizTalk applications, as well as to import existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi packages. If the creation of the applications is scripted, then the packages can be automatically built using an automated process on a build server.

For more information about scripting BizTalk application deployments, see the following documentation:

- [Deploying and Managing BizTalk Applications](/biztalk/core/deploying-and-managing-biztalk-applications)

-   [Understanding BizTalk Server Application Deployment](/biztalk/core/understanding-biztalk-application-deployment-and-management)

    > [!NOTE]
    >  This latter article also applies to BizTalk Server.

## See Also
 [Checklist: Configuring BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)