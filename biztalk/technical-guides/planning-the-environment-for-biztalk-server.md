---
title: "Planning the Environment for BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e9ef0b4-eccb-47e2-bbb5-e859ffa0468c
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning the Environment for BizTalk Server
The planning section of the operations guide describes roles and responsibilities associated with a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. It includes planning recommendations for the application and data tiers of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, and it provides planning recommendations for the release management stages of a BizTalk solution.  
  
 As the saying goes, "If you fail to plan, you plan to fail." While there are certainly exceptions to this sage advice, successful implementation of a production BizTalk solution is not one of them. This introductory topic to the planning section provides a high-level overview of the decisions you should make when planning your BizTalk solution.  
  
## Deciding Whether BizTalk Server Is the Right Tool for the Job  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be thought of as a "business integration engine." At its core, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is designed to integrate disparate business systems, processes, and messages. For example, a business system that exchanges messages that adhere to the EDI standard may need to integrate with a business system that exchanges messages that conform to the RosettaNet standard. Or an internal business system that uses SAP may need to communicate with another internal business system that stores data in a Microsoft SQL Server database. Or perhaps a business system that can only send or receive messages using the FTP protocol needs to exchange messages with a business system that can only use the HTTP protocol.  
  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] accommodates the integration of such disparate systems by acting as the middleman for message delivery between the systems. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports a wide range of industry-standard transport protocols, document exchange formats, and line of business applications.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] also provides powerful business process automation capabilities in the BizTalk Orchestration engine. You use BizTalk Orchestration Designer to create visual representations of business processes which can be built into executable code that is run in the BizTalk Orchestration engine.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] also includes several other features that facilitate business integration including a message workflow engine, a Business Rule Engine (BRE), and technologies for information workers such as Business Activity Monitoring (BAM).  
  
 For more information about using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] business process management functionality, see [White Paper: Microsoft and BPM—Technical Overview](http://go.microsoft.com/fwlink/?LinkId=106015) (<http://go.microsoft.com/fwlink/?LinkId=106015>). To know more about the different integration technologies offered by Microsoft and the advantages one has over the other, see [Understanding Microsoft Integration Technologies](http://go.microsoft.com/fwlink/?LinkId=158452) (<http://go.microsoft.com/fwlink/?LinkId=158452>).  
  
 Certain integration scenarios are better suited to other Microsoft products. If your primary focus is upon any of the following scenarios, consider using these Microsoft products instead of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
|**Scenario**|**Product to use**|  
|------------------|------------------------|  
|User provisioning|**Microsoft Identity Lifecycle Manager 2010**<br /><br /> For more information about Microsoft Identity Lifecycle Manager 2010, see [Microsoft Identity Lifecycle Manager 2010 FP1](http://go.microsoft.com/fwlink/?LinkId=204577) (http://go.microsoft.com/fwlink/?LinkId=204577).|  
|Data replication between systems|**SQL Server Replication**<br /><br /> For more information about SQL Server replication, see [SQL Server 2008 R2 Replication](http://go.microsoft.com/fwlink/?LinkID=69978) (http://go.microsoft.com/fwlink/?LinkID=69978).|  
|Data extraction, transform, and load (ETL)|**SQL Server Integration Services (SSIS)**<br /><br /> For more information about SQL Server Integration Services, see [SQL Server 2008 R2 Integration Services](http://go.microsoft.com/fwlink/?LinkId=152044) (http://go.microsoft.com/fwlink/?LinkId=152044).|  
  
## Deciding Which Edition of BizTalk Server Is Right for the Job  
 There are four different editions of BizTalk Server, each of which is targeted at specific scenarios. The four editions of BizTalk Server include:  
  
- **Enterprise** - Designed for customers with enterprise-level requirements for high volume, reliability, and availability.  
  
- **Standard** - Designed for businesses with moderate volume and deployment scale requirements.  
  
- **Branch** - Specialty version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] designed for hub and spoke deployment scenarios including RFID.  
  
- **Developer** - Provides all of the functionality of the Enterprise Edition for development and testing purposes and is available as the BizTalk Server Evaluation Edition at no cost for evaluation purposes. When installed as the Evaluation Edition, BizTalk Server will function for 120 days.  
  
- **RFID Enterprise** - Designed to provide a scalable, extensible platform for development, deployment, and management of rich RFID and sensor solutions, includes BizTalk RFID Server and BizTalk RFID Mobile.  
  
  For more information about the different editions of BizTalk Server, see [Microsoft BizTalk Server Editions](http://go.microsoft.com/fwlink/?LinkId=108051) (http://go.microsoft.com/fwlink/?LinkId=108051).  
  
## Planning for Message Load  
 Once you have determined that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] meets your business integration needs, the next thing that you should determine is the message load that the BizTalk solution will be expected to process. This is an important decision because different editions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] have different scale-up and scale-out capabilities.  
  
 The key to determine message load is to perform load testing to determine the Maximum Sustainable Throughput (MST) and the Maximum Sustainable Tracking Throughput (MSTT) of the BizTalk solution. For more information about measuring maximum sustainable throughput, and performance best practices in general, see the [BizTalk Server 2009 Performance Guide](http://go.microsoft.com/fwlink/?LinkID=150492) (http://go.microsoft.com/fwlink/?LinkID=150492).  
  
## Planning for Expansion  
 Consider implementing a BizTalk solution using the Enterprise edition of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] if you will be adding a significant number of trading partners, will need to use host clustering, or will need to scale out to multiple computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the BizTalk group. The Standard and Branch editions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not accommodate multiple computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a group or host clustering.  
  
## In This Section  
  
-   [BizTalk Server Roles and Responsibilities](../technical-guides/biztalk-server-roles-and-responsibilities.md)  
  
-   [Planning the BizTalk Server Tier](../technical-guides/planning-the-biztalk-server-tier.md)  
  
-   [Planning the Database Tier](../technical-guides/planning-the-database-tier.md)  
  
-   [Planning the Development, Testing, Staging, and Production Environments](../technical-guides/planning-the-development-testing-staging-and-production-environments.md)