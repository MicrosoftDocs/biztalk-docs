---
title: "Condition Evaluation and Action Execution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Action stage [Business Rules Engine]"
  - "examples, business rules"
  - "Business Rules Engine, policies"
  - "Match stage [Business Rules Engine]"
  - "business rules, examples"
  - "Business Rules Engine, algorithm"
  - "Business Rules Engine, examples"
  - "conflict resolution [Business Rules Engine]"
  - "Business Rules Engine, stages"
ms.assetid: dcaa32c2-3403-4f54-92e2-128686bfc193
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Condition Evaluation and Action Execution
The Business Rules Framework provides a highly efficient inference engine capable of linking rules to .NET objects, XML documents, or database tables.  
  
 The Business Rule Engine uses a three-stage algorithm for policy execution. The stages are as follows:  
  
- **Match**. In the match stage, facts are matched against the predicates that use the fact type (object references maintained in the rule engine's working memory) using the predicates defined in the rule conditions. For the sake of efficiency, pattern matching occurs over all the rules in the policy, and conditions that are shared across rules are matched only once. Partial condition matches may be stored in working memory to expedite subsequent pattern-matching operations. The output of the pattern-matching phase consists of updates to the rule engine agenda.  
  
- **Conflict resolution**. In the conflict resolution stage, the rules that are candidates for execution are examined to determine the next set of rule actions to execute based on a predetermined resolution scheme. All candidate rules found during the matching stage are added to the rule engine's agenda.  
  
   The default conflict resolution scheme is based on rule priorities within a policy. The priority is a configurable property of a rule in the Business Rule Composer. The larger the number, the higher the priority; therefore if multiple rules are triggered, the higher-priority actions are executed first.  
  
- **Action**. In the action stage, the actions in the resolved rule are executed. Note that rule actions can assert new facts into the rule engine, which causes the cycle to continue. This is also known as forward chaining. It is important to note that the algorithm never preempts the currently executing rule. All actions for the rule that is currently firing will be executed before the match phase is repeated. However, other rules on the agenda will not be fired before the match phase begins again. The match phase may cause those rules on the agenda to be removed from the agenda before they ever fire.  
  
  The following example shows the three-stage algorithm of match-conflict resolution-action.  
  
  **Rule 1: Evaluate income**  
  
- Declarative representation:  
  
   An applicant's credit rating should be obtained only if the applicant's income-to-loan ratio is less than 0.2.  
  
- IF—THEN representation using business objects:  
  
  ```  
  IF Application.Income / Property.Price < 0.2    
  THEN Assert new CreditRating( Application)   
  ```  
  
  **Rule 2: Evaluate credit rating**  
  
- Declarative representation:  
  
   An applicant should be approved only if the applicant's credit rating is more than 725.  
  
- IF—THEN Representation using business objects:  
  
  ```  
  IF Application.SSN = CreditRating.SSN AND CreditRating.Value > 725    
  THEN SendApprovalLetter(Application)    
  ```  
  
  The facts are summarized in the following table.  
  
|Fact|Fields|  
|----------|------------|  
|Application – An XML document representing a home loan application|-   Income = $65,000<br />-   SSN = XXX-XX-XXXX|  
|Property – An XML document representing the property being purchased|-   Price = $225,000|  
|CreditRating – An XML document containing the loan applicant's credit rating|-   Value = 0 – 800<br />-   SSN = XXX-XX-XXXX|  
  
 Initially the rule engine working memory and agenda are empty. After the application adds the Application and Property facts, the rule engine working memory and agenda are updated as follows.  
  
|Working memory|Agenda|  
|--------------------|------------|  
|-   Application<br />-   Property|Rule 1|  
  
 Rule 1 is added to the agenda because its condition (Application.Income / Property.Price < 0.2) evaluated to **true** during the match phase. There is no CreditRating fact in working memory, so the condition for Rule 2 was not evaluated. Because the only rule in the agenda is Rule 1, the rule is executed and then disappears from the agenda. The single action defined for Rule 1 results in a new fact (CreditRating document for the applicant) being added to working memory. After the execution of Rule 1 completes, control returns to the match phase. Because the only new object to match is the CreditRating fact, the results of the match phase are as follows.  
  
|Working memory|Agenda|  
|--------------------|------------|  
|-   Application<br />-   Property<br />-   CreditRating|Rule 2|  
  
 At this point Rule 2 is executed, resulting in the invocation of a function that sends an approval letter to the applicant. After Rule 2 has completed, execution of the forward-chaining algorithm returns to the match phase. Because there are no longer new facts to match and the agenda is empty, forward chaining terminates and policy execution is complete.  
  
## See Also  
 [Rule Engine](../core/rule-engine.md)