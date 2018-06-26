---
title: "Short-Term Facts vs. Long-Term Facts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "facts, short-term"
  - "facts, long-term"
  - "short-term facts"
  - "business rules, facts"
  - "long-term facts"
ms.assetid: de020b20-1012-498a-969e-4adc4549918c
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Short-Term Facts vs. Long-Term Facts
Two types of facts are asserted into the working memory of the rule engine—short-term facts and long-term facts.  
  
## Short-Term Facts  
 A short-term fact is specific to a single execution cycle of the rule engine. Short-term facts are retracted automatically from the working memory of the rule engine after the policy executes. If your data changes between execution cycles of the rule engine for a policy, you submit the data as a short-term fact to the rule engine.  
  
 Examples of short-term facts are:  
  
-   The facts you submit as parameters to the **Policy.Execute** method.  
  
-   The facts you submit as parameters to the **Call Rules** shape.  
  
-   The facts you submit from an action of a rule using the **Assert** function.  
  
## Long-Term Facts  
 A long-term fact is loaded into the working memory of the rule engine for use over an arbitrary number of execution cycles. Typically, long-term facts are slowly changing facts that do not typically change between executions of a policy. For example, you may want to create a database connection only once, and execute the policy several times by using the same database connection. The only real distinction between short-term facts and long-term facts is in implementation.  
  
 To submit a fact as a long-term fact, you need to perform the following steps:  
  
1. Create a fact retriever component that implements the **IFactRetriever** interface. Create and assert the fact into the working memory of the rule engine when the **UpdateFacts** method is invoked for the first time, and update the fact when necessary on subsequent invocations of the **UpdateFacts** method.  
  
2. Configure the policy to use the fact retriever component by using the Business Rule Composer.  
  
   For more information about creating a fact retriever and using it in a policy, see [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md).  
  
## See Also  
 [Facts](../core/facts.md)