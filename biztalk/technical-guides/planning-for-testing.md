---
title: "Planning for Testing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca2f5f29-9eea-4f4d-9781-75c231db4605
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Testing
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] testing can be divided into several categories including unit testing, functional testing, load testing, and availability testing. This topic describes unit and load testing and how to plan for each.  
  
## Planning for Unit Testing  
 Unit testing is a procedure used to validate that individual units of code are working as designed. Unit testing can be thought of as "break/fix" testing: Does the software perform the desired functionality under different conditions and can the software handle errors that occur under these conditions?  
  
 Since unit testing is typically performed on individual components, the associated test bed does not need the processing capabilities of an actual production environment. For this reason, you should consider performing unit testing in a Virtual Server environment, which requires considerably fewer hardware resources.  
  
 Another aspect of unit testing that may be performed in a virtualized environment is staging. Staging is the process of unit testing the actual deployment of a BizTalk solution. To maximize available hardware resources, consider using Virtual Server for your staging environment.  
  
 For more information about using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a virtual environment, see [Using Virtual Server During the Release Management Process](../technical-guides/planning-the-development-testing-staging-and-production-environments.md#BKMK_VirtualServ). For information about tools that may be useful for unit testing a BizTalk solution, see [Tools for Testing](~/technical-guides/tools-for-testing.md). For a checklist of considerations for performing unit testing see [Performing Unit Testing](../technical-guides/performing-unit-testing.md).  
  
## Planning for Load Testing  
 Load testing is the process of measuring maximum sustainable performance and maximum sustainable tracking performance of a BizTalk solution and then removing bottlenecks that inhibit the throughput of the solution. For more information about load testing and removing bottlenecks from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution, see the [BizTalk Server 2009 Performance Guide](http://go.microsoft.com/fwlink/?LinkID=150492) (<http://go.microsoft.com/fwlink/?LinkID=150492>).  
  
 For information about tools that may be useful for load testing a BizTalk solution, see [Tools for Testing](~/technical-guides/tools-for-testing.md). For a checklist of considerations for load testing see [Performing Load and Throughput Testing](../technical-guides/performing-load-and-throughput-testing.md).  
  
## Plan to Test for the Lifetime of the Solution  
 While unit testing and load testing are particularly important during the early stages of the solution, plan regular testing throughout the lifetime of the solution to uncover potential problems that may occur as load increases or as new functionality or components are added to the solution.  
  
## See Also  
 [Planning the BizTalk Server Tier](../technical-guides/planning-the-biztalk-server-tier.md)   
 [Checklist: Testing Operational Readiness](../technical-guides/checklist-testing-operational-readiness.md)