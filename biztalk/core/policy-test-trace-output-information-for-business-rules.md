---
title: "Policy Test Trace Output Information for Business Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "testing, business rules"
  - "testing, policies"
  - "business rules, testing"
  - "policies, testing"
ms.assetid: 26ff584e-97a1-4d76-a8a9-a55b4c99231f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Policy Test Trace Output Information for Business Rules
This section provides information on the tracking information that is displayed when testing a policy in the Business Rule Composer. Very similar information is seen when viewing tracking results for policy execution using the message event and service instance tracking queries on the Group Hub page.  
  
 There are four statement types that are displayed in the tracking output:  
  
- Fact Activity  
  
- Condition Evaluation  
  
- Agenda Update  
  
- Rule Fired  
  
  Each statement type is described below.  
  
## Fact Activity  
 This statement indicates changes to the facts present in the working memory of the engine. The following is an example of a fact activity entry:  
  
```  
FACT ACTIVITY 3/16/2004 9:50:28 AM  
Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
Ruleset Name: LoanProcessing  
Operation: Assert  
Object Type: MyTest.test  
Object Instance Identifier: 872  
```  
  
### Rule Engine Instance Identifier  
 Unique identifier for the **RuleEngine** instance that provides the execution environment for the rule firing.  
  
### Ruleset Name  
 The name of the rule set (policy).  
  
### Operation  
 There are three types of operation that can occur in a fact activity:  
  
 Assert  
  
 The fact is being added to the working memory.  
  
 Update  
  
 The fact is being updated by a rule and then needs to be reasserted into the engine to be re-evaluated, based on the new data and state.  
  
 Retract  
  
 The fact is being removed from the working memory.  
  
> [!NOTE]
>  If a fact is asserted whose type does not match any of the types used in the policy, the Assert operation will display "Assert – Fact Unrecognized".  
  
### Object Type  
 The type of fact for a particular activity:  
  
-   DataConnection  
  
-   TypedDataTable  
  
-   TypedDataRow  
  
     When a TypedDataTable is asserted all of the contained rows are asserted as TypedDataRows.  TypedDataRows associated with a DataConnection are not asserted until a condition is evaluated and the resulting query is executed.  
  
-   TypedXmlDocument  
  
     Assertions will be seen for both parent and child TypedXmlDocument instances.  
  
### Object Instance Identifier  
 Unique instance ID of the fact reference.  
  
## Condition Evaluation  
 This activity indicates the result of evaluating individual predicates. The following is an example of a condition evaluation entry:  
  
```  
CONDITION EVALUATION TEST (MATCH) 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Test Expression: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:Root.EmploymentType/TimeInMonths >= 18  
Left Operand Value: 31  
Right Operand Value: 18  
Test Result: True  
```  
  
 The descriptions for some of the terms in the preceding example are as follows:  
  
-   **Test Expression.** A simple (unary or binary) expression within a rule.  
  
-   **Left Operand Value.** The value of the term on the left side of an expression.  
  
-   **Right Operand Value.** The value of the term on the right side of an expression.  
  
-   **Test Result.** The result of the evaluation, which is either True or False.  
  
## Agenda Update  
 This activity indicates rules that are added to the rule engine agenda for subsequent execution. The following is an example of an agenda update entry:  
  
```  
AGENDA UPDATE 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Operation: Add  
Rule Name: Employment Status Rule  
Conflict Resolution Criteria: 0  
```  
  
 The descriptions for some of the terms in the preceding example are as follows:  
  
-   **Operation.** Rules can be added or removed from the agenda.  
  
-   **Rule Name.** The name of the rule that is being added to the agenda.  
  
-   **Conflict Resolution Criteria.** The priority of a rule, which determines the relative order in which actions are executed (higher-priority actions are executed first).  
  
## Rule Fired  
 This activity indicates the execution of a rule's actions. The following is an example of a rule fired entry:  
  
```  
RULE FIRED 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Rule Name: Residency Status Rule  
Conflict Resolution Criteria: 10  
```