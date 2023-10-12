---
description: "Learn more about: Policies"
title: "Policies"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Policies
A policy is a logical grouping of rules. You compose a version of a policy, save it, test it by applying it to facts, and, when you are satisfied with the results, publish it and deploy it to a production environment.  
  
## Policy Composition  
 You can compose policies in the Business Rule Composer by constructing rules from facts and definitions. A policy can contain an arbitrarily large set of rules, but typically you compose a policy from rules that pertain to a specific business domain within the context of the application that will be using the policy.  
  
## Policy Testing  
 You can effectively perform a test run of your policy before it is published and deployed in a production environment. The Business Rule Composer allows you to supply instances of facts to a policy, run the policy, and view its output. The output includes fact activity, rule execution, condition evaluation, and updates to the agenda.  
  
## Policy Versions  
 After you have defined all the rules in your policy, you can publish the policy version. In this way the policy is locked down, and its behavior is well-defined.  
  
 A given policy version can be used under a given set of circumstances in your business environment, and replaced by another version when those circumstances change. Also, both new and old versions can be used simultaneously by different applications.  
  
## Policy Deployment  
 When your policy is ready to be run in a production environment, you can deploy it to make it available to a hosting application.  
  
## Dynamic Policy Updates  
 Dynamic policy updates allow you to modify policies independently of a running business process. You can create and deploy an updated version of the policy, and the hosting application can incorporate the update in near real time. This update does not require you to change any code, and thus you can avoid the overhead of redeveloping and redeploying the application.  
  
## See Also  
 [Business Rules Engine](../core/business-rules-engine.md)
