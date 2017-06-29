---
title: "BizTalk Server 2010 Operations Guide | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4dc0d8e9-9ad6-4ce1-8ca7-399b67cb360e
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server 2010 Operations Guide
Welcome to the Microsoft® BizTalk® Server 2010 Operations Guide. We created this guide to be a valuable resource for anyone involved in the implementation and administration of a BizTalk solution, particularly IT professionals.  
  
 To download a copy of this guide in chm, pdf, or docx form, go to [Microsoft BizTalk Server 2010 Operations Guide](http://go.microsoft.com/fwlink/?LinkId=212652) (http://go.microsoft.com/fwlink/?LinkId=212652).  
  
## Which Versions of BizTalk Server Does the Guide Cover?  
 This guide caters to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and provides operational readiness information to help you jumpstart with your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup.  
  
> [!NOTE]
>  To see the Operations Guide for [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] or [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)], see [http://go.microsoft.com/fwlink/?LinkID=130458](http://go.microsoft.com/fwlink/?LinkID=130458).  
  
## Where Do I Start?  
 We organized the guide according to the functional aspects of planning, deploying, and managing a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation. You can therefore read it according to these functional aspects. However, realizing that the checklists would be the most sought after information in the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Operations Guide, we have categorized all the checklists in the document in the following table for ease of accessibility.  
  
|||  
|-|-|  
|**Setting Up Your BizTalk Environment**|**Setting Up a High Availability and Disaster Recovery Environment**|  
|-   [Checklist: Getting Started with BizTalk Server](../Topic/Checklist:%20Getting%20Started%20with%20BizTalk%20Server.md)<br />-   [Checklist: Configuring Windows Server](../Topic/Checklist:%20Configuring%20Windows%20Server.md)<br />-   [Checklist: Configuring Internet Information Services](../Topic/Checklist:%20Configuring%20Internet%20Information%20Services.md)<br />-   [Checklist: Configuring SQL Server](../technical-guides/checklist-configuring-sql-server.md)<br />-   [Checklist: Configuring BizTalk Server](../Topic/Checklist:%20Configuring%20BizTalk%20Server.md)|-   [Checklist: Providing High Availability with Fault Tolerance or Load Balancing](../Topic/Checklist:%20Providing%20High%20Availability%20with%20Fault%20Tolerance%20or%20Load%20Balancing.md)<br />-   [Checklist: Increasing Availability with Disaster Recovery](../Topic/Checklist:%20Increasing%20Availability%20with%20Disaster%20Recovery.md)|  
|**Monitoring, Testing, and Troubleshooting**|**Performance and Maintenance**|  
|-   [Checklist: Monitoring Operational Readiness](../Topic/Checklist:%20Monitoring%20Operational%20Readiness.md)<br />-   [Checklist: Maintaining and Troubleshooting BizTalk Server Databases](../technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)<br />-   [Checklist: Testing Operational Readiness](../Topic/Checklist:%20Testing%20Operational%20Readiness.md)<br />-   [Checklist: Monitoring BizTalk Server with Operations Manager 2007](../Topic/Checklist:%20Monitoring%20BizTalk%20Server%20with%20Operations%20Manager%202007.md)<br />-   [Checklist: Monitoring SQL Servers](../Topic/Checklist:%20Monitoring%20SQL%20Servers.md)|Maintenance related checklists:<br /><br /> -   [Checklist: Performing Daily Maintenance Checks](../Topic/Checklist:%20Performing%20Daily%20Maintenance%20Checks.md)<br />-   [Checklist: Performing Weekly Maintenance Checks](../Topic/Checklist:%20Performing%20Weekly%20Maintenance%20Checks.md)<br />-   [Checklist: Performing Monthly Maintenance Checks](../Topic/Checklist:%20Performing%20Monthly%20Maintenance%20Checks.md)<br /><br /> Performance related checklists:<br /><br /> -   [Checklist: Performing Weekly Performance Checks](../Topic/Checklist:%20Performing%20Weekly%20Performance%20Checks.md)<br />-   [Checklist: Performing Monthly Performance Checks](../Topic/Checklist:%20Performing%20Monthly%20Performance%20Checks.md)|  
|**Checklists for Other Important Tasks**||  
|-   [Checklist: Deploying an Application](../Topic/Checklist:%20Deploying%20an%20Application.md)<br />-   [Checklist: Exporting Bindings from One Application to Another](../Topic/Checklist:%20Exporting%20Bindings%20from%20One%20Application%20to%20Another.md)<br />-   [Checklist: Updating an Assembly](../Topic/Checklist:%20Updating%20an%20Assembly.md)<br />-   [Checklist: Updating Artifacts in a BizTalk Application](../Topic/Checklist:%20Updating%20Artifacts%20in%20a%20BizTalk%20Application.md)|-   [Checklist: Updating an Application Using Side-by-Side Versioning](../Topic/Checklist:%20Updating%20an%20Application%20Using%20Side-by-Side%20Versioning.md)<br />-   [Checklist: Updating an Orchestration Using Side-by-Side Versioning](../Topic/Checklist:%20Updating%20an%20Orchestration%20Using%20Side-by-Side%20Versioning.md)<br />-   [Checklist: Installing and Configuring Certificates](../technical-guides/checklist-installing-and-configuring-certificates.md)<br />-   [Checklist: Planning for Operations in a Secure Environment](../technical-guides/checklist-planning-for-operations-in-a-secure-environment.md)|  
  
 If you are performing the following tasks, you can start with the related sections:  
  
-   **Evaluating operational readiness**: If you are focused on assessing and evaluating the operational readiness of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment, then start by reading the [Operations Checklists](../Topic/Operations%20Checklists.md) and [Increasing Availability for BizTalk Server](../Topic/Increasing%20Availability%20for%20BizTalk%20Server.md) sections.  
  
-   **Becoming operationally ready**: To ensure that your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] infrastructure and applications become operationally ready, refer to the [Planning the Environment for BizTalk Server](../Topic/Planning%20the%20Environment%20for%20BizTalk%20Server.md) section.  
  
-   **Maintaining an operational environment**: Most of the topics in the operations guide assist you in maintaining an operational [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. You will find best practices, key concepts, and procedures for maintaining an operational environment in the following sections: [Increasing Availability for BizTalk Server](../Topic/Increasing%20Availability%20for%20BizTalk%20Server.md), [Monitoring BizTalk Server](../Topic/Monitoring%20BizTalk%20Server2.md), and [Maintaining BizTalk Server2](../Topic/Maintaining%20BizTalk%20Server2.md).  
  
## What's in It?  
 Guidance based on real-world experience. The idea for the guide originated with Microsoft field representatives, partner organizations, and customers who plan, deploy, and maintain BizTalk Server installations. This group of IT professionals has accumulated extensive hands-on experience with a diverse range of BizTalk solutions. As they gained experience they created checklists, best practices, and presentations to guide future [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] operations. We collected and organized this information to create the guide.  
  
 Key portions of this guide are new; however, a considerable portion refers to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help, white papers, Knowledge Base articles, and other sources. It has been carefully reviewed and vetted by experts from the community of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] IT professionals and members of the product development team, whom we gratefully acknowledge at the end of this topic. We believe that the information presented here will help [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] users solve, and above all, avoid many of the common problems that can occur while deploying and maintaining a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.  
  
## Acknowledgments  
 We in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] User Education team gratefully acknowledge the outstanding contributions of the following individuals for providing both technical feedback as well as a good deal of content for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operations Guide:  
  
-   Paolo Salvatori, Tim Wieman