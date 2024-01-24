---
description: "Learn more about: Performance Considerations When Using the Rule Engine"
title: "Performance Considerations When Using the Rule Engine"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Performance Considerations When Using the Rule Engine
This topic discusses how the rule engine performs in various scenarios and with different values for the configuration/tuning parameters.  
  
## Fact Types  
 The rule engine takes less time to access .NET facts than it does to access XML and database facts. If you have a choice of using .NET, XML, or database facts in a policy, you should consider using .NET facts for better performance.  
  
## Data Table vs. Data Connection Binding  
 When the size of the data set is small (fewer than approximately 10 rows), the **TypedDataTable** binding performs better than the **DataConnection** binding. When the data set is large (greater than or equal to approximately 10 rows), the **DataConnection** binding performs better than the **TypedDataTable** binding. Therefore, you should decide whether to use the **DataConnection** binding or the **TypedDataTable** binding based on the estimated size of the data set.  
  
## Fact Retrievers  
 You can write a fact retriever—an object that implements standard methods and typically uses them to supply long-term and slowly changing facts to the rule engine before the policy is executed. The engine caches these facts and uses them over multiple execution cycles. Instead of submitting a static or fairly static fact each time you invoke the rule engine, you should create a fact retriever that submits the fact the first time, and then updates the fact in memory only when it is needed.  
  
## Rule Priority  
 The priority setting for a rule can range on either side of **0**, with larger numbers having higher priority. Actions are executed in order from highest priority to lowest priority. When the policy implements forward-chaining behavior by using **Assert/Update** calls, the chaining can be optimized by using the priority setting. For example, suppose that **Rule2** has a dependency on a value that is set by **Rule1**. Giving **Rule1** a higher priority means that **Rule2** will execute only after **Rule1** fires and updates the value. Conversely, if **Rule2** is given a higher priority, it can fire once, and then fire again after **Rule1** fires and updates the fact that **Rule2** is using in a condition. This may or may not produce the correct results, but clearly firing twice has a performance impact versus firing only once.  
  
## Update Calls  
 The **Update** function updates a fact that exists in the working memory of the rule engine, and causes all the rules that use the updated fact in conditions to be reevaluated. **Update** function calls can be expensive, especially if many rules need to be reevaluated because of updating the facts. There are situations where you can avoid having to reevaluate the rules. For example, consider the following rules:  
  
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
  
 All remaining rules of the policy use **StatusObj.Flag** in their conditions. Therefore, when **Update** is called on the **StatusObj** object, all the rules will be reevaluated. Whatever the value of the **Amount** field is, all the rules except **Rule1** and **Rule2** are evaluated twice, once before the **Update** call and once after the **Update** call.  
  
 Instead, you could set the value of the **flag** field to **false** before you invoke the policy and then use only **Rule1** in the policy to set the flag. In this case, **Update** is called only if the value of the **Amount** field is greater than 5, and **Update** is not called if the amount is less than or equal to 5. Therefore, all the rules except **Rule1** and **Rule2** are evaluated twice only if the value of the **Amount** field is greater than 5.  
  
## Use of Logical OR Operators  
 The rule engine is optimized for executing logical **AND** operators and it reconstructs the rule it parsed in a disjunctive normal form so that **OR** operator is used only at the top level. Using an increasing number of logical **OR** operators in conditions creates additional permutations that expand the analysis network of the rule engine, and It may take long time for the rule engine to normalize the rule. The following list contains possible workarounds for this issue.  
  
-   Modify the rule to be in disjunctive normal form so that the **OR** operator is only at the top level. Note that developing a rule in disjunctive normal form in Business Rule Composer can be tricky. You may want to consider creating the rule programmatically.  
  
-   Develop a helper component that performs the **OR** operations and returns a Boolean value, and use the component in the rule.  
  
-   Consider splitting the rule into multiple rules and have the rules check for a flag set by a previously executed rule or use an object that is asserted by a previously executed rule as shown in the following examples:  
  
    -   Rule 1: IF (a == 1 OR a == 3) THEN b = true  
  
         Rule 2: if (b == true) THEN …  
  
    -   Rule 1: IF (a == 1 OR a == 3) THEN assert(new c())  
  
         Rule 2: IF (c.flag == true) THEN …  
  
## Caching Settings  
 The rule engine uses two caches. The first one is in the Update service and the second one is in each BizTalk process. The first time a policy is used, the BizTalk process requests the policy information from the Update service. The Update service retrieves the policy information from the Rule Engine database, caches it, and returns the information to the BizTalk process. The BizTalk process creates a policy object based on that information and stores the policy object in a cache when the associated rule engine instance completes executing the policy. When the same policy is invoked again, the BizTalk process reuses the policy object from the cache if one is available in the cache.  
  
 Similarly, if the BizTalk process requests the information about a policy from the Update service, the Update service first looks for the policy information in its cache. The Update service also checks every 60 seconds (one minute) to see if there have been any updates to the policy in the database. If there are any updates, the Update service retrieves the information and caches the updated information.  
  
 There are three tuning parameters for the rule engine related to these caches: **CacheEntries**, **CacheTimeout**, and **PollingInterval**. You can specify the values for these parameters either in the registry or in a configuration file.  
  
 The value of **CacheEntries** is the maximum number of entries in the cache. The default value of **CacheEntries** is 32. You may want to increase the value of the **CacheEntries** parameter to improve performance in some cases. For example, suppose you are using 40 policies repeatedly. In this case you may want to increase the value of **CacheEntries** to 40 to improve performance. This would allow the Update service to cache details of up to 40 policies in memory. It would also cause the BizTalk service to cache up to 40 policy instances in memory. There may be more than one instance of a policy in the cache of the BizTalk service.  
  
 The value of **CacheTimeout** is the time (in seconds) for entries to age out of the Update service cache. In other words, the **CacheTimeout** value refers to how long a cache entry for a policy is kept in the cache if there are no references to it. The default value of **CacheTimeout** is 3600 seconds (one hour). This means that, if the cache entry is not referenced within an hour, it is deleted. In some cases, you may want to increase the **CacheTimeout** value to improve performance. For example, suppose the policy is invoked every two hours. You could improve the performance of the policy execution by increasing the value of the **CacheTimeout** parameter to a value greater than two hours.  
  
 The **PollingInterval** parameter for the rule engine defines the time in seconds for the interval at which the Update service checks the Rule Engine database for updates. The default value for the **PollingInterval** parameter is 60 seconds (one minute). If you know that the policies do not get updated at all or are updated rarely, you could increase this value to improve performance.  
  
## SideEffects Property  
 The **ClassMemberBinding**, **DatabaseColumnBinding**, and **XmlDocumentFieldBinding** classes have a property named **SideEffects**. This property determines whether the value of the bound field, member, or column is cached. The default value of the **SideEffects** property in the **DatabaseColumnBinding** and **XmlDocumentFieldBinding** classes is **false**. The default value of the **SideEffects** property in the **ClassMemberBinding** class is **true**. Therefore, when a field of an XML document or a column of a database table is accessed for the second time or later within the policy, its value is retrieved from the cache. However, when a member of a .NET object is accessed for the second time or later, the value is retrieved from the .NET object, and not from the cache. Setting the **SideEffects** property of a .NET **ClassMemberBinding** to **false** will improve performance because the value of the field is retrieved from the cache from the second time onwards. You can only do this programmatically. The Business Rule Composer tool does not expose the **SideEffects** property.  
  
## Instances and Selectivity  
 The **XmlDocumentBinding**, **ClassBinding**, and **DatabaseBinding** classes have two properties: **Instances** and **Selectivity**. The value of **Instances** is the expected number of instances of the class in working memory. The value of **Selectivity** is the percentage of the class instances that will successfully pass the rule conditions. The rule engine uses these values to optimize the condition evaluation so that the fewest possible instances are used in condition evaluations first and then the remaining instances are used. If you have prior knowledge of the number of instances of the object, setting the **Instances** property to that value would improve performance. Similarly, if you have prior knowledge of the percentage of these objects passing the conditions, setting the **Selectivity** property to that value would improve performance. You can only set values for these parameters programmatically. The Business Rule Composer tool does not expose them.
