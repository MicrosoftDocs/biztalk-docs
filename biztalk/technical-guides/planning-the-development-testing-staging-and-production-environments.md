---
title: "Planning the Development, Testing, Staging, and Production Environments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c83a42d-117f-4a24-a669-b3e4e1c9a056
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning the Development, Testing, Staging, and Production Environments
This topic discusses the environments used in the release management process for a BizTalk solution. As with any enterprise software solution, you should follow established software release management guidelines when you develop and release a BizTalk solution. This process should include the following distinct stages:  
  
- Development  
  
- Testing  
  
- Staging  
  
- Production  
  
  Ideally, you should complete each stage in the release management process in a discrete environment, separate from the other environments. Realistically, you may have to combine one or more of the environments due to hardware, time, or other resource constraints. At a bare minimum you should separate the production environment from the other environments.  
  
> [!NOTE]
>  The latest installation and upgrade instructions for BizTalk Server are listed at [BizTalk Server What's New, Installation, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md). 
> 
> ##  <a name="BKMK_VirtualServ"></a> Using Virtual Server During the Release Management Process  
>  Consider completing development, unit testing, and staging in a "virtual" environment. Performing development work, unit testing, and staging in a virtual environment offers great flexibility and uses considerably fewer hardware resources than required otherwise. If a virtual environment is used, allocate at least 512 MB of memory for each virtual machine that is running on the host computer and an additional 512 MB of memory for the host operating system.  
  
 For example, for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment that uses five virtual machines (two computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], two Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster nodes, and one domain controller), you would plan to have 3 GB of memory installed on the host computer. If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment requires more than 2 GB of memory, consider installing a 64-bit version of Windows on the host computer to ensure that the maximum amount of installed memory is accessible by the host operating system.  
  
> [!NOTE]
>  For recommendations on using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a virtual environment, see [BizTalk Server 2009 Hyper-V Guide](http://go.microsoft.com/fwlink/?LinkId=151834) (<http://go.microsoft.com/fwlink/?LinkId=151834>).  
> 
> [!NOTE]
>  BizTalk Server is fully supported on a supported operating system that is running on any of the virtualization software listed in the Microsoft Knowledge Base Article 842301 [Microsoft BizTalk Server supportability on a virtual machine](https://support.microsoft.com/kb/842301). However, BizTalk Server may not perform as expected if installed on a supported operating system that is running in a virtualization software other than the ones mentioned in the KB article.  
  
## Development Environment  
 The BizTalk projects that are used for the BizTalk solution are created in the development environment. You should install the following software on the computers used in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development environment:  
  
- Internet Information Services (IIS)  
  
- Visual Studio  
  
- SQL Server Client Tools  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (including the following components)  
  
  -   Documentation  
  
  -   Administrative tools  
  
  -   Developer tools and SDK  
  
  -   Additional software  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], if the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are to be hosted locally during development.  
  
- Typically developers should have their own development computer (physical or virtual) with the necessary software installed.  
  
> [!NOTE]  
>  We recommend that you purchase and use Visual Studio subscription for non-production environments. Visual Studio subscriptions are offered at a significant discount from the cost of a retail license for the same software. See [Visual Studio Subscriptions](https://visualstudio.com/subscriptions).  
  
## Testing Environment  
 Unit testing can be completed in a virtual environment. You should, however, conduct your performance testing in a physical environment with hardware and software that is identical to the production environment.  
  
 The testing environment is used to measure performance characteristics such as maximum sustainable throughput (MST) and maximum sustainable tracking throughput of the BizTalk solution. It should therefore match the physical production environment as closely as possible. For more information about measuring performance characteristics of a BizTalk solution see [Engine Performance Characteristics](../core/engine-performance-characteristics.md), or the [BizTalk Server Performance Optimization Guide](../technical-guides/biztalk-server-2010-performance-optimization-guide.md).
  
## Staging Environment  
 You typically use the staging environment to "unit test" the actual deployment of the BizTalk solution. The software installed in the staging environment should closely match the software installed in the production environment. It may, however, be acceptable to use virtual computers in the staging environment since this environment is not to be used for measuring performance. For more information about deploying a BizTalk application to a staging environment see [Staging Tasks for BizTalk Application Deployment](../core/staging-tasks-for-biztalk-application-deployment.md).
  
## Production Environment  
 The production environment is the "live" environment that will host the running BizTalk solution. The production environment is the final endpoint in the release management process and should only host BizTalk applications that have previously undergone development, unit testing, load testing, and staging in the other environments. Thorough unit testing, load testing, and staging beforehand will help ensure maximum performance and uptime for the BizTalk application in the production environment.  
  
## Guidelines for Allocating Servers  
 The following guidelines provide a rule of thumb for the number of BizTalk servers and SQL servers you should allocate to each stage in the release management process given a particular number of physical computers expected to be used in production: They are rough estimates which are subject to change depending on your architecture.  
  
> [!NOTE]  
>  Virtual servers may be used in the development and in the staging environment and can also be used for unit testing. All performance testing should be performed on physical hardware that matches the physical hardware in the production environment.  
  
|Computers running BizTalk Server used in production (physical hardware recommended)|Development servers (virtual or physical hardware)|Testing servers (physical hardware recommended)|Staging servers (virtual or physical hardware)|Total no. of computers running BizTalk Server|  
|---|---|---|---|---|  
|1|2|1|1|5|  
|2|2|2|1|7|  
|3|2|3|1|9|  
|4|2|4|1|11|  
  
|Estimated no. of computers running SQL Server used in production (physical hardware recommended)|Development servers (virtual or physical hardware)|Testing servers (physical hardware recommended)|Staging servers (virtual or physical hardware)|Total no. of computers running SQL Server|  
|---|---|---|---|---|  
|1|1|1|1|4|  
|2|1|2|1|6|  
|3|2|3|1|9|  
|4|2|4|1|11|  
  
## See Also  
 [Planning the Environment for BizTalk Server](../technical-guides/planning-the-environment-for-biztalk-server.md)