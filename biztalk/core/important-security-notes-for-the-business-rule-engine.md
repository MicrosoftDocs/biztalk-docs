---
description: "Learn more about: Important Security Notes for the Business Rule Engine"
title: "Important Security Notes for the Business Rule Engine | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business rules, store administrator"
  - "Business Rule Composer, security"
  - "business rules, security"
  - "Denial of Service attacks"
ms.assetid: 8972127a-5569-4b32-bc09-e9265efe9514
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Important Security Notes for the Business Rule Engine
This topic summarizes known security issues in Microsoft BizTalk Server and the steps you must take to mitigate the security risks.  
  
## Malicious schema input causing Denial of Service attack  
 While asserting facts, each rule is verified against every object that matches the supported types within a policy. Suppose there is a rule in a policy that uses one of the elements in a schema passed by using a selector. Now if the instance if this element/attribute that matches the selector is repeated thousands of times, every such instance is asserted, causing performance degradation and subsequent possible Denial of Service (DoS).  
  
 To mitigate this potential issue, you need to validate all ambiguous input that is passed while executing a policy.  
  
## RuleSet not validating objects before asserting the facts  
 Any schema instance passed as a fact to the **RuleSet** is not validated against the schema before asserting any rules using selectors. You should validate all input that is passed while executing a policy.  
  
## Expected behaviors of the Business Rule Composer when RuleStore security is on  
 You can enable the role-based security feature for the rule store by calling the **EnableAuthorization** method of the **RuleStore** class. When this security feature is enabled, the expected behaviors in the Business Rule Composer are as follows:  
  
-   The object model filters out rule sets and vocabularies to which the user does not have read access. Therefore, they do not appear in the Business Rule Composer.  
  
-   If the user does not have write access to a policy or a vocabulary, any save attempt causes an exception to be thrown.  
  
## User types for rule store administrator  
 The rule store administrator has the privilege to define an authorization group for artifacts saved in the rule store. However, note the following differences between two types of user to which the rule store administrator can belong:  
  
-   When the rule store administrator is a Windows user, which means using Windows authentication to connect the rule store, the rule store administrator can define an authorization group whose user is a Windows group or a Windows user.  
  
-   When the rule store administrator is a SQL user, which means using SQL authentication to connect the rule store, the rule store administrator cannot define an authorization group whose user is a Windows group, but can define an authorization group whose user is a Windows user.  
  
## User cannot associate an authorization group with an artifact without sufficient rights  
 An artifact creator that is neither a SQL dbo user nor a member of RE_ADMIN_USERS, and does not have MODIFY_DELETE permission to an artifact, cannot associate a new authorization group with the artifact. The following scenario is an example of this behavior:  
  
1.  Rule set creator is not dbo, is not in the RE_ADMIN_USERS group, and does not have MODIFY_DELETE permission after the rule set is created.  
  
2.  Creator creates a rule set.  
  
3.  Member of the RE_ADMIN_USERS group creates authorization AG1 with MODIFY_DELETE permission to User2.  
  
4.  Creator associates AG1 with the rule set.  
  
5.  Enable the rule store authorization.  
  
6.  Member of the RE_ADMIN_USERS group creates authorization AG2 with READ_EXECUTE permission to User2.  
  
7.  Creator associates AG2 with the rule set. Although the creator does not have sufficient right to do so, no error message appears.  
  
8.  Attempt to read the rule set by User2 fails.
