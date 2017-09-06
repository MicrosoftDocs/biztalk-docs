---
title: "Implementation Phase Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04877156-cc32-480b-8410-d26eb073c327
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implementation Phase Recommendations
The implementation phase takes the requirements and design phase products and implements them using appropriate technologies. In the case of validation testing, it is during this phase that test cases are completed and automated in preparation for validation testing. Typically, a lot of testing on the early system versions is also performed during this phase, not only to validate the system, but to validate that there are no problems with the test cases themselves.  
  
## Implement Performance Test Cases  
 During the requirements and design phases, representative test cases were defined and designed to prove the performance of the system meets or exceeds the performance release criteria. During the implementation phase, these test cases are implemented, automated, and initially executed to verify that, as various parts of the system reach code complete, testing is ready to verify performance.  
  
 It is important to automate the setup, running, and results analysis of the tests during the implementation phase as much as possible. The number of performance tests can be large and individual tests can take a long time to run, so having the tests automated will increase the efficiency of running them, reducing the number of required human resources. In addition, anticipate running the verification tests many times during a test pass as performance bottlenecks are identified and fixes provided. Having the tests automated makes it easier, faster, and more consistent to re-run performance verification between builds.  
  
## Build the Performance Test Bed  
 It is extremely important that all performance testing is performed in a consistent, reproducible way. Using the same exact hardware on which to establish baselines and run tests is key if the results of those tests are to be comparable. Depending on your solution architecture, there are a wide variety of hardware variables that can significantly affect the results.  
  
 For example, we have found that the memory cache available, even on otherwise identical servers, significantly affects results even though it may not be immediately apparent from looking at the server configuration that two servers have different levels of cache. Making sure tests are run on test beds that are not changed between runs can eliminate any question of comparability. If you must change the hardware configuration, such as when adjusting for a new system size estimate, then baselines should be re-established so that comparisons can be made.  
  
## Begin Performance Validation Testing  
 Performance testing almost always begins in parallel with the test implementation.  It is almost never too early to begin validating the release criteria since the sooner you start, the sooner you can react if issues are discovered.  
  
 The primary consideration when beginning formal testing is the readiness of the system, or part of the system, being tested. System readiness is very much a judgment call, but should include consideration for the following factors:  
  
 Is the system pathway you are about to test code complete? If there is significant code yet to be added to the pathway, you may want to consider focusing efforts elsewhere until a "critical mass" is ready.  
  
 Have functional tests been successfully run on the system? It can be very time consuming and inefficient to set up and begin performance testing on a system or subsystem only to find out that there is something functionally wrong that blocks further performance testing. Make sure the pathway has been sufficiently functionally tested before starting performance testing.  
  
 What is the level of risk for the system or subsystem to be tested? The first system pathways to be investigated should be those that carry the highest level of risk with regard to meeting performance release criteria. The importance of identifying system bottlenecks early enough in the project life cycle to allow for time to change course cannot be over stated.  
  
## See Also  
 [Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md)   
 [Requirements Phase Recommendations](../core/requirements-phase-recommendations.md)   
 [Design Phase Recommendations](../core/design-phase-recommendations.md)   
 [Verification Phase Recommendations](../core/verification-phase-recommendations.md)   
 [Release Phase Recommendations](../core/release-phase-recommendations.md)