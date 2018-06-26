---
title: "Design Phase Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee3d183e-a6f3-47d0-90ac-99b12c064607
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Design Phase Recommendations
The primary deliverables for the design phase are design specifications for both the system and the test cases for validating system functionality and performance. Investigations of the feasibility of features and tests are a typical part of the design process, involving initial development and, in the case of validation design, some early testing of proof-of-concept implementations as discussed in this section below.  
  
## Acquire Detailed Throughput and Latency Profiles  
 Building on the initial load profiles on which the performance release criteria from the previous project phase were established, establish detailed throughput and latency profiles during the design phase. If available, acquire performance data from production systems. Using production data will provide realistic performance profiles on which test cases can be designed during this phase. If production data is not available, then a realistic profile must be extrapolated from expected load.  
  
 It is critical that the performance test cases being created during the design phase include performance profiles that closely emulate what the system will be expected to support in production. For more information about creating realistic and sustainable performance profiles, see [What Is Sustainable Performance?](../core/what-is-sustainable-performance.md)  
  
## Investigate Performance Risk Mitigations  
 During the requirements phase, risks to achieving the desired performance goals were identified and possible mitigations identified.  The risks and mitigations should be investigated as early in the design phase as possible in order to allow time to change the design if needed. Each identified risk should first be proven to be an issue using proof of concept (POC) testing and then mitigations should be tested to evaluate efficacy.  
  
 For example, assume that a legacy system uses FTP to communicate with other systems. However, looking at the level of throughput that the legacy FTP server can achieve in combination with the BizTalk Server FTP adapter, it is clear that the desired throughput (established as release criteria during the requirements phase) will not be achievable. To mitigate the risk to the project, the following alternatives are identified during the requirements phase:  
  
- Scale up or out the FTP server and create multiple logical FTP addresses dedicated to specific message types to spread the load  
  
- Modify the legacy system to deliver many messages in a single file as a batch to reduce the per-message transfer overhead  
  
- Modify the legacy system to use an alternative protocol that is known to be faster than FTP such as MSMQ  
  
  The first investigation that needs to be done in this example is to prove that the risk exists by testing the current FTP system performance. A simple proof of concept solution that just receives messages from the FTP server would be built and deployed and the production load profile expected for the FTP pathway applied to it. If the server is capable of sustaining the desired load, then the risk is not realized and further investigation is not needed. If it is not able to sustain the desired load, then the alternative that is most likely to address the issue with the least amount of cost and project risk should be investigated via a proof of concept investigation.  
  
## Refine System Size Estimate  
 Investigations conducted during the design phase provide valuable empirical information regarding the performance capabilities of your system.  
  
 For example, let's continue the example above where the performance of FTP is found to be too low. Because the environment already includes systems that use MSMQ as a messaging transport, it was decided to modify the legacy system to use MSMQ as well. However, during the performance testing of a new POC that employs MSMQ, it was observed that the CPU on the SQL server on which the MessageBox database lives almost constantly at 100% utilization and you are not able to achieve the expected throughput on the MSMQ pathway.  
  
 Assuming the SQL Server configuration is optimal for the application, the SQL Server hardware is clearly undersized for the desired throughput and the system size needs to be refined. In this case, the SQL Server hardware needs either additional CPUs, faster CPUs, or both.  
  
## See Also  
 [Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md)   
 [Requirements Phase Recommendations](../core/requirements-phase-recommendations.md)   
 [Implementation Phase Recommendations](../core/implementation-phase-recommendations.md)   
 [Verification Phase Recommendations](../core/verification-phase-recommendations.md)   
 [Release Phase Recommendations](../core/release-phase-recommendations.md)