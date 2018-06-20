---
title: "How to Develop Interdependent Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5464096e-66d8-48de-bc02-c754c5cfbada
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Develop Interdependent Orchestrations
You can use [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] to develop a set of orchestrations that have interdependent Web services. This scenario arises when you have orchestrations that reference data types and/or ports in the orchestration from which they were called. An example of this type of scenario is characterized by the following:  
  
- You have two or more orchestrations.  
  
- The first orchestration (Orch1) calls the second orchestration (Orch2) with a one-way Web service call.  
  
- Orch2 responds back to Orch1 with a Web service call.  
  
  For one example of this type of project, see [Tutorial 2: Purchase Order Process](http://msdn.microsoft.com/library/a324ef1b-39b3-49ab-9719-a13f526cb467).  
  
### To develop two interdependent orchestrations Orch1 and Orch2  
  
1. Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a partial version of the Orch1 that has a receive port which will be exposed as a Web service.  
  
2. Compile Orch1.  
  
3. Run the Web Services Publishing Wizard and publish the port.  
  
4. Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create and complete all of Orch2, consuming Orch1's web service.  
  
5. Compile Orch2.  
  
6. Run the Web Services Publishing Wizard and publish the port(s).  
  
7. Complete Orch1, consuming Orch2's web service(s) as needed.  
  
8. Recompile Orch1.  
  
9. Deploy Orch1 and Orch2.  
  
## See Also  
 [How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)