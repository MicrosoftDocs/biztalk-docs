---
title: "Manage the BAM Portal in BizTalk Server| Microsoft Docs"
description: Overview of installing and configuring the BAM portal in BizTalk Server
ms.custom: ""
ms.date: "08/15/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a08aa85-3a45-4a8c-bdb5-5615ca097ce1
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manage the BAM portal

## Set up BAM portal
Administrators set up the BAM portal by running the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation. Use the BizTalk Server configuration tool to specify whether BAM is enabled, and to specify the Web service accounts, the Windows groups that can view portal, and the Web site that will host the portal. If it becomes necessary to update the BAM portal configuration once you have set up the BAM portal, you use the configuration tool to update the configuration settings such as the portal users group, the Application Pool account, and the management Web services user.

 For more information about installing the BAM portal, see [Install and Configure BAM in Multiple Computer Environments](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx).

 For more information about configuring the BAM portal, see [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).

 The BAM portal has many customizable settings that are accessed by modifying the webconfig.xml file. These settings control the performance and operation of the BAM portal. This rest of this section describes how to customize your BAM portal configuration.

## Next steps

-   [Customizing the BAM Portal Configuration](../core/customizing-the-bam-portal-configuration.md)

-   [How to Configure the BAM Portal to Work on an NLB Cluster](../core/how-to-configure-the-bam-portal-to-work-on-an-nlb-cluster.md)

## See Also
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)
