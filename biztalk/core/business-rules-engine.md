---
description: "Learn more about: Business Rules Engine"
title: "Business Rules Engine"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Business Rules Engine
The Business Rules Framework is a Microsoft .NET-compliant class library. It provides an efficient inference engine that can link highly readable, declarative, semantically rich rules to any business objects (.NET components), XML documents, or database tables. Application developers can build business rules by constructing rules from small building blocks of business logic (small rule sets) that operate on information (facts) contained in .NET objects, database tables, and XML documents. This design pattern promotes code reuse, design simplicity, and modularity of business logic. In addition, the rule engine does not impose on the architecture or design of business applications. In fact, you can add rule technology to a business application by directly invoking the rule engine, or you can have external logic that invokes your business objects without modifying them. In short, the technology enables developers to create and maintain applications with minimal effort.  
  
 In planning development of a rule-based application, you first need to determine how rules will fit into your business processes. Your application will create an instance of a policy and supply it with data, or facts, on which to operate. The policy object encapsulates the rule engine and provides a single point of entry through which to run it.  
  
 You also will need to plan for the development and testing of your rules design. You must consider how you are going to deploy and update your policies. You will likely want to track the progress of your rule engine's execution and monitor its current state.  
  
 Account for the following steps as you plan your rules development:  
  
1.  Plan how to incorporate your rules into your application.  
  
2.  Identify the business logic that you want to represent with rules in your application. The term "business logic" can refer to many things; an example of business logic is "Purchase orders for more than five hundred dollars must be approved by a manager."  
  
3.  Identify data sources for your rule elements. You can optionally define and publish vocabularies (domain-specific nomenclature that represents underlying bindings).  
  
4.  Define rules from vocabulary definitions or directly from data bindings, and from them compose a policy that represents your business logic.  
  
    > [!NOTE]
    >  Vocabularies must be published before they can be applied in rules.  
  
5.  Test and debug the policy with sample facts. You can either use the Test Policy functionality in the Business Rule Composer or use **Policy** or **PolicyTester** classes to execute from an application, command-line program, or orchestration.  
  
6.  Publish the policy version to the rule store.  
  
7.  Deploy the policy version.  
  
8.  Instantiate and build the short-term fact list in the hosting application. Use the **Call Rules** shape in an orchestration to execute your business policy or programmatically instantiate a policy version in your hosting application.  
  
9. Monitor and track rule execution as needed.  
  
    > [!NOTE]
    >  The default tracking interceptor works with orchestrations. If your hosting application is not an orchestration, you must write your own tracking interceptor to do this.  
  
## In This Section  
  
-   [Rules](../core/rules.md)  
  
-   [Policies](../core/policies.md)  
  
-   [Vocabularies](../core/vocabularies.md)  
  
-   [Business Rules Framework Architecture](../core/business-rules-framework-architecture.md)  
  
-   [Facts](../core/facts.md)  
  
-   [Rule Engine](../core/rule-engine.md)
