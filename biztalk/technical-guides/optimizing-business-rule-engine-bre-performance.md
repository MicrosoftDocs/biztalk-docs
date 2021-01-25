---
description: "Learn more about: Optimizing Business Rule Engine (BRE) Performance"
title: "Optimizing Business Rule Engine (BRE) Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c271b059-174d-4e8b-88b5-c3f408a97f1f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optimizing Business Rule Engine (BRE) Performance
The following factors should be considered when implementing the Business Rule Engine (BRE) in a BizTalk Server solution:  
  
## Fact types  
 The rule engine takes less time to access .NET facts compared to the time it takes to access XML and database facts. If you have a choice of using either .NET or XML or database facts in a policy, you should consider using .NET facts for improved performance.  
  
## Data table vs. data connection  
 When the size of the data set is small (< 10 or so), the **TypedDataTable** binding provides better performance than the **DataConnection** binding. However, the **DataConnection** binding performs better than the **TypedDataTable** binding when the data set is large (greater than or equal to 10 rows approximately). Therefore, you should decide whether to use the **DataConnection** binding or **TypedDataTable** binding based on the estimated size of the data set.  
  
## Fact retrievers  
 A fact retriever implements standard methods which are typically used to supply long-term and slowly changing facts to the rule engine before a policy is executed. The engine caches these facts and uses them over multiple execution cycles. Instead of submitting a static or fairly static fact each time that you invoke the rule engine, you should create a fact retriever that submits the fact for the first time, and then updates the fact in memory only when necessary.  
  
## Rule priority  
 The priority setting for a rule can range on either side of **0**, with larger numbers having higher priority. Actions are executed in order from the highest priority to lowest priority. When the policy implements forward-chaining behavior by using **Assert/Update** calls, the chaining can be optimized by using the priority setting. For example, assume that **Rule2** has a dependency on a value set by **Rule1**. Giving **Rule1** a higher priority means that **Rule2** will only execute after **Rule1** fires and updates the value. Conversely, if **Rule2** were given a higher priority, it could fire once, and then fire again after **Rule1** fires and update the fact that **Rule2** is using a condition. While this may provide a correct result, giving **Rule1** a higher priority in this scenario will provide better performance.  
  
## Update calls  
 The Update function causes all the rules using the updated facts to be reevaluated. Update function calls can be expensive especially if a large set of rules is reevaluated when updating facts. There are situations where this behavior can be avoided. For example, consider the following rules.  
  
 **Rule1:**  
  
```  
IF PurchaseOrder.Amount > 5   
THEN StatusObj.Flag = true; Update(StatusObj)  
```  
  
 **Rule2:**  
  
```  
IF PurchaseOrder.Amount <= 5   
THEN StatusObj.Flag = false; Update(StatusObj)  
```  
  
 All remaining rules of the policy use **StatusObj.Flag** in their conditions. Therefore, when **Update** is called on the **StatusObj** object, all rules will be reevaluated. Whatever the value of the **Amount** field is, all rules except **Rule1** or **Rule2** are evaluated twice, once before the **Update** call and once after the **Update** call.  
  
 To mitigate the associated overhead, you could set the value of the **flag** field to **false** prior to invoking the policy and then use only **Rule1** in the policy to set the flag. In this case, **Update** would be called only if the value of the **Amount** field is greater than 5, and the **Update** function is not called if the value of **Amount** is less than or equal to 5. Therefore, all the rules except **Rule1** or **Rule2** are evaluated twice only if the value of the **Amount** field is greater than 5.  
  
## Usage of logical OR operators  
 Using an increasing number of logical OR operators in conditions creates additional permutations that expand the analysis network of the rule engine. From a performance standpoint, you are better off splitting the conditions into atomic rules that do not contain logical OR operators.  
  
## Caching settings  
 The Rule Engine uses two caches. The first one is used by the update service and the second one is used by each BizTalk process. The first time a policy is used, the BizTalk process requests the policy information from the update service. The update service retrieves the policy information from the rule engine database, caches it and returns the information to the BizTalk process. The BizTalk process creates a policy object based on that information and stores the policy object in a cache when the associated rule engine instance completes execution of the policy. When the same policy is invoked again, the BizTalk process reuses the policy object from the cache if one is available. Similarly, if the BizTalk process requests information about a policy from update service, the update service looks for the policy information in its cache if it is available. Every 60 seconds, the update service also checks if there have been any updates to the policy in the database. If there are any updates, the update service retrieves the information and caches the updated information.  
  
 There are three tuning parameters for the rule engine related to these caches: **CacheEntries**, **CacheTimeout**, and **PollingInterval**. You can specify the values for these parameters either in the registry or in a configuration file. The value of the **CacheEntries** parameter is the maximum number of entries in the cache and is set to a value of 32 by default. You may want to increase the value of the **CacheEntries** parameter to improve performance in certain scenarios. For example, say you are using 40 policies repeatedly; you could to increase the value of the **CacheEntries** parameter to 40 to improve performance. This would allow the update service to maintain cache details of up to 40 policies in memory.  
  
 The value of **CacheTimeout** is the time in seconds that an entry is maintained in the update service cache. In other words, the **CacheTimeout** value refers to how long a cache entry for a policy is maintained in the cache without being referenced. The default value of **CacheTimeout** parameter is 3600 seconds, or 1 hour. It means that if the cache entry is not referenced within an hour, the entry is deleted. In some cases, it may be beneficial to increase the value of the **CacheTimeout** parameter to improve performance. For example, if a policy is invoked every two hours, performance of the policy execution would be improved by increasing the **CacheTimeout** parameter to a value higher than two hours.  
  
 The **PollingInterval** parameter of the rule engine defines the time in seconds for the update service to check the rule engine database for updates. The default value for the **PollingInterval** parameter is 60 seconds. If you know that the policies do not get updated at all or are updated rarely, you could change this parameter to a higher value to improve performance.  
  
## SideEffects property  
 The **ClassMemberBinding**, **DatabaseColumnBinding**, and **XmlDocumentFieldBinding** classes have a property named **SideEffects**. This property determines whether the value of the bound field, member, or column is cached. The default value of the **SideEffects** property in the **DatabaseColumnBinding** and **XmlDocumentFieldBinding** classes is **false**. The default value of the **SideEffects** property in the **ClassMemberBinding** class is **true**. Therefore, when a field of an XML document or a column of a database table is accessed for the second time or later within the policy, its value is retrieved from the cache. However, when a member of a .NET object is accessed for the second time or later, the value is retrieved from the .NET object, and not from the cache. Setting the **SideEffects** property of a .NET **ClassMemberBinding** to **false** will improve performance because the value of the field is retrieved from the cache from the second time onwards. You can only do this programmatically. The Business Rule Composer tool does not expose the **SideEffects** property.  
  
## Instances and selectivity  
 The **XmlDocumentBinding**, **ClassBinding**, and **DatabaseBinding** classes have two properties: **Instances** and **Selectivity**. The value of Instances is the expected number of instances of the class in working memory. The value of **Selectivity** is the percentage of the class instances that will successfully pass the rule conditions. The rule engine uses these values to optimize the condition evaluation so that the fewest possible instances are used in condition evaluations first and then the remaining instances are used. If you have prior knowledge of the number of instances of the object, setting the **Instances** property to that value would improve performance. Similarly, if you have prior knowledge of the percentage of these objects passing the conditions, setting the **Selectivity** property to that value would improve performance. You can only set values for these parameters programmatically. The Business Rule Composer tool does not expose them.  
  
## See Also  
 [Optimizing BizTalk Server Performance](../technical-guides/optimizing-biztalk-server-performance.md)
