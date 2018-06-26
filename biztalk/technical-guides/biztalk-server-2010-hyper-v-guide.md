---
title: "BizTalk Server 2010 Hyper-V Guide | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c38ecdd-de72-41d9-b639-2aa6bbfee917
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server 2010 Hyper-V Guide
The purpose of this guide is to provide practical guidance for using Microsoft BizTalk Server with Microsoft [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Hyper-V. The emphasis is on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], but the performance evaluation methods and performance testing scenarios are useful for analyzing the performance of virtualized server applications in general. This guidance will be of interest to both the IT Pro and Developer communities.  

 To download a copy of this guide, go to [http://go.microsoft.com/fwlink/?LinkId=149267](http://go.microsoft.com/fwlink/?LinkId=149267).  

## Introduction  
 Server virtualization offers companies the opportunity to run multiple operating systems on a single physical machine. This enables the consolidation of underutilized servers onto a smaller number of fully utilized machines. By implementing virtualization, companies can minimize operational and capital expenditure costs associated with deploying and operating the servers required for enterprise applications.  

 The potential costs savings has prompted IT departments to evaluate new and existing applications to identify candidates suitable for server virtualization. Most such evaluations seek to discover the total cost of virtualization. The total cost of virtualization is the sum of monetary costs for hardware and IT operations, and the performance cost of virtualization as compared to the performance attainable in a physical environment. This guide focuses exclusively on the performance aspect of virtualization.  

 Beginning with Windows Server 2008, server virtualization using Hyper-V technology has been an integral part of the operating system. [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Hyper-V provides a reliable and optimized virtualization solution enabling organizations to improve server utilization and reduce costs. With the addition of new features such as live migration functionality, expanded processor and memory support for host systems, support for dynamic virtual machine storage, it allows organizations to consolidate workloads onto a single physical server and is a good solution for organizations who are consolidating servers as well as for development and test environments.  

 BizTalk Server takes advantage of the latest virtualization improvements included as part of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Hyper-V, which can lead to reduced costs through production server consolidation and business continuity management, plus the creation of a more dynamic IT infrastructure. The Clustering capability allows BizTalk Server to be deployed in multi-site clustering environments without additional software or hardware. Hyper-V provides support to run several instances of BizTalk Server on virtualized instances of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Server Virtualization enables BizTalk customers to minimize the hardware footprint of a BizTalk deployment by consolidating underutilized resources in a secure manner.  

 A BizTalk Server deployment typically consists of a number of other components including: SQL Server, Windows Server and Internet Information Services (IIS). Hyper-V provides support for dynamic provisioning through System Center Virtual Machine Manager (VMM) which makes provisioning on demand a realistic scenario.  

 [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] provides the Hyper-V technology to accommodate server consolidation through virtualization of multiple operating system instances onto a single physical server. Hyper-V is provided as a core part of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] or as a stand-alone product to make it as easy as possible for customers to embrace virtualization in their organization. There are several key scenarios for implementing Hyper-V:  

- **Server Consolidation** – Minimize server footprint, operational and capital expenditure (TCO) associated with running applications by consolidating multiple physical servers onto one box.  

- **Testing and Development** – Using virtual machines, developers and architects can quickly provision new machines to try out new technology and scenarios in a safe environment that accurately reflects the characteristics of a physical environment. Virtualization enables new machines to be provisioned running on a wide platform of operating systems without new hardware being required. This provides a great platform for testing and development environments.  

- **Business Continuity and Disaster Recovery** – Hyper-V includes powerful business continuity and Disaster Recovery features such as live backup and quick migration which enables businesses to meet their service level agreements.  

  > [!NOTE]  
  >  For information about how to back up Hyper-V virtual machines using Windows Server Backup, see Microsoft Knowledge Base article 958662, “How to back up Hyper-V virtual machines from the parent partition on a Windows Server 2008-based computer by using Windows Server Backup” at [http://go.microsoft.com/fwlink/?LinkId=131207](http://go.microsoft.com/fwlink/?LinkId=131207).  
  >   
  >  For information about how to use the Hyper-V Live Migration Feature available in Windows Server 2008 R2, see “Hyper-V: Step-by-Step Guide to Using Live Migration in Windows Server 2008 R2” at [http://go.microsoft.com/fwlink/?LinkID=139667](http://go.microsoft.com/fwlink/?LinkID=139667).  

- **Dynamic Data Center** – By combining Hyper-V with the Microsoft System Center suite of tools, organizations can automate virtual machine configuration and monitoring. For more information, see “System Center Virtual Machine Manager” at [http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303).  

  The information in this guide directly relates to the Server Consolidation and Testing and Development scenarios for Hyper-V. The other two were out of scope for this guide.  

  For more information about core scenarios for Hyper-V, see [Virtualization with Hyper-V: Overview](http://go.microsoft.com/fwlink/?LinkID=202438) and the topics in the [Appendices1](../technical-guides/appendices1.md) section of this guide.  

### Who Should Read This?  

- All IT Professionals who work with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  

- IT Professionals who deploy, optimize and maintain an application environment  

- IT Professionals who work with development teams to evaluate and optimize system architectures  

- Developers who create and maintain [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications  

- Developers interested in performance optimization and identifying performance bottlenecks  

### Goals of this Guide  
 The primary goal of this guide is to provide guidance about how to determine if BizTalk Server running on Hyper-V is likely to meet performance expectations. This guidance will also be of value as an aid to optimization of a deployed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.  

 This project was conducted with the following goals:  

- Provide specific guidance for anyone who is evaluating, designing, or implementing a virtualized [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  

- Provide an introduction to the performance monitor counters and tools used to measure the performance capabilities of a virtualized server platform.  

- Provide guidelines for determining the cost of virtualization as a function of the performance difference between physical and virtualized server environments.  

- Develop best practices for use when planning or optimizing a virtualized [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  

- Provide architectural guidance to help you determine how to deploy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a virtualized environment.  

- Identify and document performance bottlenecks in a virtualized environment.  

### What’s in this Guide?  
 Guidance for implementing a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution on a Hyper-V virtualized environment. This guide includes:  

- **Deploying BizTalk Server on Hyper-V**: [Deploying BizTalk Server on Hyper-V](../technical-guides/deploying-biztalk-server-on-hyper-v.md) describes the steps that were followed to set up the lab environment used to compare the performance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution running on Hyper-V virtual machine to the same [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution running on physical hardware.  

- **Evaluating BizTalk Server Performance on Hyper-V**: [Evaluating BizTalk Server Performance on Hyper-V](../technical-guides/evaluating-biztalk-server-performance-on-hyper-v.md) details important considerations when measuring performance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution running on a Hyper-V virtualized environment.  

- **Testing BizTalk Server Performance on Hyper-V**: [Testing BizTalk Server Virtualization Performance](../technical-guides/testing-biztalk-server-virtualization-performance.md) provides detailed results of four distinct testing scenarios that compare the performance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution running on Hyper-V virtual machine to the same [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution running on physical hardware.  

- **Appendices**: The topics in [Appendices1](../technical-guides/appendices1.md) provide important reference material for this guide including:  

  -   [Appendix A: Optimizations Applied to Computers in Test Environment](../technical-guides/appendix-a-optimizations-applied-to-computers-in-test-environment.md) – Provides detailed information about the performance optimizations that were applied to the computers in the test environment.  

  -   [Appendix B: Hyper-V Architecture and Feature Overview](../technical-guides/appendix-b-hyper-v-architecture-and-feature-overview.md) - Provides an overview of Hyper-V architecture, describes advantages and disadvantages of Hyper-V, and describes differences between Hyper-V and Virtual Server 2005  

  -   [Appendix C: BizTalk Server and SQL Server Hyper-V Supportability](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md) – Describes support policies for running BizTalk Server and SQL Server on a Hyper-V virtual machine.  

  -   [Appendix D: Tools for Measuring Performance](../technical-guides/appendix-d-tools-for-measuring-performance.md) - Describes several tools that can be used to monitor and evaluate the performance of a BizTalk Server environment.  

- **Glossary**: The [Glossary8](../technical-guides/glossary8.md) defines key terms used throughout this guide.
