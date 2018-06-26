---
title: "Requirements Phase Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b510313-c3a7-42bc-9c9b-336c927a5d4a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Requirements Phase Recommendations
The primary deliverable associated with the requirements phase is a requirements specification, or a functional specification that includes requirements including performance goals. It is very important to involve the end-users and business owners of the system when determining these goals to assure that an accurate profile for performance is derived.  
  
## Establish Performance Criteria  
 From a performance perspective, the most important part of the functional specification that is created during this phase is the definition of detailed performance goals for the project and the establishment of performance release criteria. There are three critical components to defining performance criteria:  
  
- A curve that defines performance as a function of time.  
  
- A performance requirement associated with the performance function.  
  
- A distribution of file sizes and types.  
  
  These criteria are discussed in [What Is Sustainable Performance?](../core/what-is-sustainable-performance.md)  
  
  You derive the performance release criteria for an application from the performance goals. These criteria embody an achievable and measurable behavior that you can prove via testing. The application will not move into release unless and until all release criteria have been met or, if not achievable, identified as exceptions to the release criteria.  
  
  It is very important to set the release criteria during the early phases of the product cycle. Doing so means everyone involved knows what the goals are and the consequences of not reaching them before design and implementation are signed off.  
  
  In addition, performance test cases will be based on how the release criteria are to be measured, so the criteria must be detailed enough to avoid confusion. For example, when stating a specific throughput is to be achieved, it should include:  
  
- The hardware on which it must run, for example, the number and type of servers, disk speed/type, etc.  
  
- What scenario is to be tested, for example, what path messages will take through the application  
  
- How it is to be measured, for example, performance counters, custom code, measuring times messages arrive in a share, etc.  
  
  To judge how well formed a release criteria is, anyone should be able look at the release criteria as documented and understand how to build a test case to prove the criteria.  
  
## Identify Performance Risks  
 After the performance release goals and criteria have been sufficiently detailed, an initial assessment of performance risk areas can be performed. The purpose of this analysis is to identify parts of the application that may need special design attention, work-around alternatives or elimination in order to reach the desired criteria.  
  
 For example, each transport adapter type has its own performance and scale characteristics. If the desired throughput exceeds the ability of one or more of the adapter types (either receive or send), then alternatives for scaling the adapter may need to be investigated.  
  
## Estimate Sizing  
 Based on the established goals and criteria, it is never too early to begin the process of estimating the hardware sizing that will be required to meet the goals. As with any sizing estimation efforts, one must base the estimates on actual test results. During the early phases of a project, those results must come from external sources. You can read case studies at BizTalk Server Developer Center, at [http://go.microsoft.com/fwlink/?LinkId=49339](http://go.microsoft.com/fwlink/?LinkId=49339). The case studies provide details about the scenarios tested, the hardware on which testing was done, and the configuration for the tests. You can extrapolate from the performance achieved for these test cases to get an initial sizing estimate for your system.  
  
 Keep in mind that there is no predictive model or simulation that accurately predicts system size for any arbitrary application running on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is a platform on which a large variety of application solutions can be deployed, each with its own performance behavior. So, while an estimate derived using existing case study results will provide a good starting point for planning purposes, the final size of the system will most certainly need to be adjusted for all but the simplest application architectures.  
  
## Plan for Sufficient Testing  
 As stated above, there is currently no model or simulation that will accurately predict the hardware required to meet performance goals. This means that the only way to actually prove a system is capable of reaching goals is to test it on production-level hardware. That is, to conduct test cases on hardware that is as close to the production setup as possible.  
  
 This part of the planning is critical and pulls together the principles of sustainable performance, understanding throughput profiles in detail, and the performance release criteria. Using the throughput profiles obtained by extrapolating from existing data, test cases must be derived that will consistently measure the release criteria. The test cases must be run with sustainability in mind. For examples of sustainable testing, see the following topics:  
  
-   [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md)  
  
-   [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)  
  
## See Also  
 [Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md)   
 [Design Phase Recommendations](../core/design-phase-recommendations.md)   
 [Implementation Phase Recommendations](../core/implementation-phase-recommendations.md)   
 [Verification Phase Recommendations](../core/verification-phase-recommendations.md)   
 [Release Phase Recommendations](../core/release-phase-recommendations.md)