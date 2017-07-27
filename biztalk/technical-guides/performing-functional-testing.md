---
title: "Performing Functional Testing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b9c8c95-5a25-4255-a4c2-e26c67b7a620
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Performing Functional Testing
You use functional testing to test a specific end-to-end scenario or a given use case in the context of a particular BizTalk application. A functional test should cover all the possible paths through a given scenario, including the failure paths. Failure paths should be evaluated to ensure that the application deals with failure conditions appropriately.  
  
 All the artifacts (such as orchestrations, custom pipeline components, and custom assemblies) should be invoked, and all the code branches through these objects should be tested as well. All the possible combinations of messages should be exercised to ensure that messages flow through the system correctly. Invalid messages should be tested as well to make sure that the application reacts in the expected way in case of error and to test the code contained in all the exception blocks of orchestrations and custom components.  
  
## Automating Functional Testing  
 You should automate functional testing so that it is fast, so that it can be repeated, and so that it will avoid human errors. **BizUnit** is a declarative test framework designed to enable developers to rapidly design test cases. In fact, an XML configuration file called BizUnit XML test case is enough to define how a test should be performed. To run tests you can create your own custom driver or more easily leverage **Visual Studio Unit Testing** or **NUnit** to host and run your tests.  
  
 Every BizUnit XML test case contains three phases: **TestSetup**, **TestExecution**, and **TestCleanup**. Each of these phases can contain zero or more test steps. Each step represents a unit of work and is implemented as a .NET class designed to perform a certain task. This framework provides a rich set of components. If you need to realize specialized components to meet specific requirements, however, you can write your own custom test step components. For more information about these tools, see [Tools for Testing](~/technical-guides/tools-for-testing.md).  
  
> [!NOTE]  
>  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this program. Use of this program is entirely at your own risk.  
  
## See Also  
 [Checklist: Testing Operational Readiness](../technical-guides/checklist-testing-operational-readiness.md)