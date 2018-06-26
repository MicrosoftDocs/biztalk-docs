---
title: "BizTalk Server 2010 Performance Optimization Guide | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a56b27f-3e57-47db-a776-520f2d67d65e
caps.latest.revision: 31
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Server 2010 Performance Optimization Guide
Welcome to the Microsoft® BizTalk® Server 2010 Performance Optimization Guide. We created this guide to provide in-depth information for optimizing the performance of a BizTalk Server solution. Full end-to-end performance testing is frequently overlooked during enterprise application deployment. Knowing that Microsoft has built a scalable messaging infrastructure, many organizations that use BizTalk Server spend little or no time conducting performance testing of their own applications. BizTalk Server applications consist of many parts, which may include custom-built components as well as those provided by Microsoft. It is impossible for Microsoft to performance test every possible combination of these components. Therefore, fully and properly conducting a performance test of your application is a critical step of any deployment.  

 The purpose of this guide is to consolidate and provide prescriptive guidance on the best practices and techniques that should be followed to optimize BizTalk Server performance.  

 To download a copy of this guide in chm, pdf, or docx form, go to [Microsoft BizTalk Server 2010 Performance Optimization Guide](http://go.microsoft.com/fwlink/?LinkId=210870)(http://go.microsoft.com/fwlink/?LinkId=210870).  

## What's in it?  
 Generally, the performance of a server is determined by the component that has the lowest performance—the bottleneck in the system. The key to improving performance is being able to identify bottlenecks, determine their cause, and apply the appropriate corrective action.  

 As you plan your BizTalk Server deployment, use this guide to help design and optimize your environment. The concept of performance is closely related to the concept of scalability. When you have a solid understanding of the factors influencing the performance of system components, you can deploy components in a way that scales to support periods of high demand.  

 This guide provides guidance for optimizing performance, based upon hands-on experience of IT professionals who have worked extensively with BizTalk Server. Specifically, this guide includes four main sections:  

- **Finding and Eliminating Bottlenecks**: The [Finding and Eliminating Bottlenecks](../technical-guides/finding-and-eliminating-bottlenecks.md) section describes various types of performance bottlenecks as they relate to BizTalk Server solutions and information about how to resolve the bottlenecks.  

- **Optimizing Performance**: The [Optimizing Performance](../technical-guides/optimizing-performance.md) section provides guidance for optimizing performance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance is closely tied to performance of the platform upon which [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed. This section provides recommendations for optimizing performance of both [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] platform.  

- **Scaling a Production BizTalk Server Environment**: The [Scaling a Production BizTalk Server Environment](../technical-guides/scaling-a-production-biztalk-server-environment.md) section provides detailed results of BizTalk Server performance testing completed by the BizTalk product team. These tests focused on scalability and measured the impact of adding BizTalk Server computers, the impact of adding [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox databases, and the impact of adding both BizTalk Server computers and BizTalk Server MessageBox databases to a solution simultaneously.  

  - When increasing the number of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group, for these tests only one [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database was configured for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. These tests focused solely on the impact of adding [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.  

  - When increasing the number of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox databases used by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. These tests focused solely on the impact of adding [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox databases to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.  

  - When increasing the number of both [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox databases used by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group. These tests measured the impact of adding both adding [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox databases to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.  

- **BizTalk Server Performance Testing Methodology**: The [BizTalk Server Performance Testing Methodology](../technical-guides/biztalk-server-performance-testing-methodology.md) section provides detailed information about how to test and optimize [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance. It includes information about which performance criteria to focus on and the fundamental phases that should be applied when assessing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance.  

## Additions to this version of the guide  
 [Using Visual Studio to Facilitate Automated Testing](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md) – Describes the use of Visual Studio Load testing to evaluate the performance of a BizTalk Server application.  

## Acknowledgments  
 We in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] User Education team gratefully acknowledge the outstanding contributions of the following individuals for providing both technical feedback as well as a good deal of content for the BizTalk Server Performance Optimization Guide:  

 **Authors**  

- Tim Wieman, Microsoft  

- Paolo Salvatori, Microsoft  

- Trace Young, Microsoft  

  **Reviewers**  

- Tim Wieman, Microsoft  

- Paolo Salvatori, Microsoft
