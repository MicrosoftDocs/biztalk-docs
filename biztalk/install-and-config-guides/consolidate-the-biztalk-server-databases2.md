---
title: "Consolidate the BizTalk Server Databases2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7fc4fe6-3fc2-4164-9f16-90b6f473ba8c
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Consolidate the BizTalk Server Databases2
A Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation may require the creation of up to 13 separate databases in Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] for use as data stores for various [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features. Due to the overhead required to manage and maintain these databases, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] accommodates the consolidation of several of these databases into a single database. This section describes how to accomplish [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database consolidation and discusses considerations for implementing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database consolidation.  

> [!NOTE]
>  For a complete list of all of the databases that are required when installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Databases in BizTalk Server](../core/databases-in-biztalk-server.md).  

## Implementing BizTalk Database Consolidation  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database consolidation is performed after installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], during [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration. Follow these steps to implement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database consolidation:  

1. Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then click **BizTalk Server Configuration**. If prompted to select a configuration type, click **Custom configuration**.  

2. Enter the same [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]**Server Name** and **Database Name** (for example *BizTalkConsolidatedDb*) for one of more of the following data stores:  

   |Feature Name|Data Store Name|  
   |------------------|---------------------|  
   |Enterprise SSO|SSO Database|  
   |Group|BizTalk Management Database|  
   |Group|BizTalk MessageBox Database|  
   |Group|BizTalk Tracking Database|  
   |Business Rules Engine|Rule Engine Database|  

    Note that the following data stores should **not** be configured to share a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database:  


   | Feature Name |       Data Store Name       |
   |--------------|-----------------------------|
   |  BAM Tools   | BAM Primary Import Database |
   |  BAM Tools   |    BAM Archive Database     |


3. Set the remaining configuration options and apply the configuration. The configuration tool will create tables in the shared [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database for the data stores for which you specified the same [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]**Server Name** and **Database Name**.  

## Considerations for Implementing BizTalk Database Consolidation  
 When consolidating a BizTalk Database, consider the following:  

1. Database consolidation reduces the overhead associated with managing and maintaining the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases but should only be implemented in the appropriate environment. Before implementing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database consolidation in a production environment, the effect on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sustained performance should be measured in a staging environment. Consider implementing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database consolidation to simplify database administration and maintenance in the following scenarios:  

   - Small scale, low volume [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] production environments where database performance is very unlikely to become a performance bottleneck.  

   - Medium scale, medium volume [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] production environments if the BizTalk tracking database is not included in the consolidation and, ideally, if the BizTalk tracking database is created on a separate physical disk from the consolidated database.  

   - Large scale, high volume [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] production environments if the shared [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database is physically located on a very high performance storage area network (SAN) device where the likelihood of the database becoming a performance bottleneck is very low.  

   - Proof of concept or development environments where database performance is of secondary concern.  

2. Overall [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance is usually dependent upon the performance of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. Therefore database consolidation should not be implemented in any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] production environment that is experiencing or will be experiencing high volume. One exception to this is if the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are located on a very high performance storage area network (SAN) device where the likelihood of the database becoming a performance bottleneck is very low. If the database disks are not housed on a high performance SAN, distributed databases provide superior performance to consolidated databases, especially under load.  

3. If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management database is included in the database consolidation and the consolidation database is not named **BizTalkMgmtDb**, then the BizTalk Administration console must be configured to point to the consolidation database. Follow the steps in [How to Connect to an Existing Group](../core/how-to-connect-to-an-existing-group.md) and configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to point to the consolidation database in order to manage the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.  

4. For more information about sustainable [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance, please refer to [Planning for Sustained Performance](../core/planning-for-sustained-performance.md).  

   For more information about activities related to maintaining the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, please refer to [Maintaining BizTalk Server1](../core/maintaining-biztalk-server1.md).