---
description: "Learn more about: Versioning the Service Oriented Solution"
title: "Versioning the Service Oriented Solution"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Versioning the Service Oriented Solution
The two orchestrations that act as front ends to the solution, **CustomerServiceReceiveSend** and **CustomerServiceNativeRequestResponse**, call the central, working orchestration, **CustomerService**. Orchestration calls depend on the version number of the assembly containing the orchestration. Because all three orchestrations are in the same assembly, there are no versioning issues.  
  
 In addition, the business process implemented by the orchestrations is a very short-lived request-response process that completes quickly. Thus, the question of versioning the business process does not arise in this solution—there are no different orchestrations in different assemblies with different versions.  
  
 However, the orchestrations do use the schemas in the schema assembly. If the schemas are revised and compiled into a different version, you must recompile the orchestrations with the newer version of the schema assembly.  
  
## See Also  
 [Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md)
