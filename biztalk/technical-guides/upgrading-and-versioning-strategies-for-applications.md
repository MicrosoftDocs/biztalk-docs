---
description: "Learn more about: Upgrading and Versioning Strategies for Applications"
title: "Upgrade and Version Strategies for Applications"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: upgrade-and-migration-article
---
# Upgrading and Versioning Strategies for Applications
BizTalk application versioning can become an issue when you need to run two versions of a BizTalk solution side-by-side, or if you cannot use BizTalk application downtime to deploy a new version. If you do not need to run two versions of the solution simultaneously (for example, where you have no long-running orchestrations), and service maintenance windows are available, then it is perfectly acceptable to undeploy the old version, and deploy the new version as a versioning strategy (no assembly versioning). This is a possible versioning strategy, although we still recommend incrementing the file version number (to let you know what version is deployed on the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).  
  
## When to Use Versioning  
 If you need to support long-running orchestrations, and/or you need to perform BizTalk application deployments with no BizTalk application downtime, then you need to implement and practice a solid, end-to-end [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versioning strategy for the different versioning scenarios. This includes .NET assembly versioning and versioning of all BizTalk artifacts, which includes schemas, maps, pipelines, pipeline components, orchestrations, custom adapters, custom classes called in orchestrations and maps, business rules, and BAM.  
  
 Schema versioning is unique in that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipelines determine the message type of a message based on the target namespace plus root node name defined in the schema. For more information, see [Schema Resolution in Pipeline Components](../core/schema-resolution-in-pipeline-components.md). If you need to version your schemas, a version indicator must be part of the target namespace. Changing the schema version has a ripple effect throughout your solution, and therefore should be planned in advance. When creating orchestration messages, search for **BizTalk Server: 8 Tips And Tricks For Better BizTalk Programming** (tip 1: Always Use Multi-Part Message Types). Use of this method provides greater flexibility when versioning schemas.  
  
## Using Factoring for Assembly Versioning  
 If you need to support long-running orchestrations, side-by-side deployments, or no-downtime upgrades, then you should implement an assembly versioning and packaging strategy. In order to perform assembly versioning of BizTalk artifacts, your BizTalk solution assemblies need to be factored (packaged) in such a way to allow for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versioning.  There are three types of factoring:  
  
-   **No factoring**  
  
     All BizTalk artifacts are in one assembly. This is the easiest to understand and deploy, but provides the least amount of flexibility.  
  
-   **Full factoring**  
  
     Each BizTalk artifact is in its own assembly. This provides the most flexibility, but is the most complex to deploy and understand.  
  
-   **Optimal factoring**  
  
     Somewhere in-between “no factoring” and “full factoring” based on in-depth analysis of your BizTalk applications. In addition to versioning, this allows you to easily implement your BizTalk Host design. This is achieved by looking for relationships among BizTalk artifacts. Artifacts that are always versioned together can typically be put in the same assembly. If independent versioning of the artifacts is required, then they must be put in different assemblies. This is the level of factoring you want to achieve.  
  
## Additional Resources  
  
 Define and practice a solid versioning strategy to ensure it provides any side-by-side deployment strategies you might need. Resources for BizTalk Server application upgrade and versioning strategies include the following:  
  
-   [Updating an Application](../technical-guides/updating-an-application.md)  
  
-   [Updating BizTalk Applications](../core/updating-biztalk-applications.md)
  
-   [BizTalk Server Project Versioning](../core/biztalk-server-project-versioning.md)  
  
-   [Understanding BizTalk Server Application Deployment](../core/understanding-biztalk-application-deployment-and-management.md)


  
## See Also  
 [Checklist: Configuring BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)
