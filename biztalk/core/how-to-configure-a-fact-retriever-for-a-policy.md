---
description: "Learn more about: How to Configure a Fact Retriever for a Policy"
title: "How to Configure a Fact Retriever for a Policy"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Configure a Fact Retriever for a Policy
You can store facts that do not change frequently, and then before the first execution cycle of your host application, you can retrieve these facts from storage, present them once to the rule engine for caching, and reuse them over multiple execution cycles.  
  
 There are two ways to associate a fact retriever with a policy. You can do this by using the Business Rule Composer or programmatically by using the **RuleSetExecutionConfiguration** object.  
  
> [!NOTE]
>  Only one fact retriever implementation can be associated with a policy version.  
  
### To associate a fact retriever with a policy in the Business Rule Composer  
  
1.  In the Policy Explorer window, click the policy version with which you want to associate the fact retriever.  
  
2.  In the Properties window, click the **ellipsis** button (…) in the **FactRetriever** property to browse in the global assembly cache for a fact retriever object.  
  
    > [!IMPORTANT]
    >  The **ellipsis** button (…) does not appear until you click the **FactRetriever** row in the Property Window.  
  
## See Also  
 [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md)
