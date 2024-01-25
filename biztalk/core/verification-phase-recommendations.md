---
description: "Learn more about: Verification Phase Recommendations"
title: "Verification Phase Recommendations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Verification Phase Recommendations
After the system is code complete, it is ready to be fully stabilized and the release criteria can be verified. This phase is often referred to as the stabilization phase. The ultimate goal of this phase is to identify and fix bugs and prove that the system is ready for production. This phase, therefore, involves a final round of testing on a release candidate of the system.  
  
 A release candidate is a version of the system (usually the most recent) that is deemed complete and stable enough to become the released version should the verification test all pass. The way this is proven is by successful completion of a bank of functional, performance, and stress tests that verify it is indeed ready.  
  
## Test to Verify Sustainable Throughput and Latency  
 Verification testing for performance was started in parallel with the implementation phase, but needs to be finalized on a release candidate that has been shown to successfully withstand the full set of release criteria testing. Optimally, no changes to the release candidate are taken during the final test pass so that confidence is high that regressions have not been introduced. In practice, this is quite difficult and, as changes are checked into the build, evaluations must be made as to the risk of regression.  
  
 For example, if a fundamental change to a system artifact such as a pipeline or orchestration is introduced, performance tests will likely need to be re-run in order validate this new release candidate.  
  
 To ensure that the system is ready for production, you must verify that it has been tested in a sustainable fashion end to end. This means that all operations activities such as database maintenance, operations querying, and planned and unplanned outages must be tested, as defined in the topic [What Is Sustainable Performance?](../core/what-is-sustainable-performance.md) This is the last chance to certify readiness for the system, so it is important to combine the full suite of sustainable performance tests in the final test pass.  
  
## Identify Bottlenecks and Adjust Hardware or Solution to Remove Goal-Blockers  
 In practice, it is common that the test bed for the final test pass is closer to production with respect to hardware than the development of test beds.  It is important, therefore, to use the opportunity during the final test pass to identify any new or existing bottlenecks in the system and decide if they are of sufficient magnitude to require adjustments in hardware. Even if hardware doesn’t need to be adjusted immediately, identifying the most prevalent system bottlenecks will provide valuable planning and operations information.  
  
 For example, if the system sustains the production load profile, but it is observed that the physical disk idle time on the MessageBox server is low (for example, below 20%), then monitoring this disk during production can be identified as a key health indicator. In addition, any plans for increasing the load capability of the system can now include knowledge that the disk subsystem will need to be improved.  
  
## See Also  
 [Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md)   
 [Requirements Phase Recommendations](../core/requirements-phase-recommendations.md)   
 [Design Phase Recommendations](../core/design-phase-recommendations.md)   
 [Implementation Phase Recommendations](../core/implementation-phase-recommendations.md)   
 [Release Phase Recommendations](../core/release-phase-recommendations.md)
