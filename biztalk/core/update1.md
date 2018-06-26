---
title: "Update1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Update function [Business Rules Engine]"
  - "Update function [Business Rules Engine], TypedXMLDocument"
  - "Update function [Business Rules Engine], TypedData table"
  - "Update function [Business Rules Engine], .NET objects"
  - ".NET objects"
  - "Update function [Business Rules Engine], DataConnection"
ms.assetid: 939e45dc-6433-42f3-a336-8f3c247417ac
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update
When **Update** function is invoked an object, the object is reasserted into the engine to be re-evaluated, based on the new data and state. The object can be of type **TypedXmlDocument** or .NET class or **DataConnection** or **TypedDataTable**.  
  
 You can also use **Update** function to improve engine performance and prevent endless loop scenarios as described in this topic.  
  
 Typically, you use **Assert** to place a new object in the working memory of the rule engine, and use **Update** to update an already existing object in the working memory. When you assert a new object, conditions in all the rules are evaluated. When you update an existing object, only conditions that use the updated fact are reevaluated, and actions are added to the agenda if these conditions are evaluated to true.  
  
## Using Update function on .NET facts  
 Take the two rules that follow as an example. Suppose that objects **ItemA** and **ItemB** already exist in working memory. Rule 1 evaluates the **Id** property on **ItemA**, sets the **Id** property on **ItemB**, and then reasserts **ItemB** after the change. When **ItemB** is reasserted, it is treated as a new object and the engine re-evaluates all rules that use object **ItemB** in the predicates or actions. This ensures that Rule 2 is re-evaluated against the new value of **ItemB.Id**, as set in Rule 1. Rule 2 may have failed the first time it was evaluated, but evaluates to **true** the second time it is evaluated.  
  
### Rule 1  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Assert(ItemB)  
```  
  
### Rule 2  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 This ability to reassert objects into working memory allows the user explicit control over the behavior in forward-chaining scenarios. A side effect of the reassertion in this example, however, is that Rule 1 is also re-evaluated. Because **ItemA.Id** was not changed, Rule 1 again evaluates to **true** and the **Assert(ItemB)** action fires again. As a result, the rule creates an endless loop situation.  
  
> [!NOTE]
>  The default maximum loop count of re-evaluation of rules is 2^32. For certain rules, the policy execution could last for a long time. You can reduce the count by adjusting the **Maximum Execution Loop Depth** property of the policy version.  
  
 You need to be able to reassert objects without creating endless loops, and the **Update** function provides this capability. Like a reassert, the **Update** function performs **Retract** and **Assert** of the associated object instances, which have been changed from rule actions, but there are two key differences:  
  
- Actions on the agenda for rules where the instance type is only used in the actions (not the predicates) will remain on the agenda.  
  
- Rules that only use the instance type in the actions will not be re-evaluated.  
  
  Therefore, rules that use the instance types in either the predicates only or both the predicates and actions will be re-evaluated and their actions added to the agenda as appropriate.  
  
  Changing the preceding example to use the **Update** function ensures that only Rule 2 is re-evaluated because **ItemB** is used in the condition of Rule 2. Rule 1 is not reevaluated because **ItemB** is only used in the actions of Rule 1, eliminating the looping scenario.  
  
### Rule 1  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Update(ItemB)  
```  
  
### Rule 2  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 However, it is still possible to create looping scenarios. For example, consider the following rule.  
  
### Rule 1  
  
```  
IF ItemA.Id == 1  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 Because **ItemA** is used in the predicate, it is re-evaluated when **Update** is called on **ItemA**. If the value of **ItemA.Id** is not changed elsewhere, Rule 1 continues to evaluate to **true**, causing **Update** to once again be called on A. The rule designer must ensure that looping scenarios such as this are not created.  
  
 The appropriate approach for this will differ based on the nature of the rules. The following is a simple mechanism to solve the problem in the preceding example.  
  
 The **Update** function may be used in the Business Rule Composer with a reference to the class, as with the **Assert**, **Retract**, or **RetractByType** functions.  
  
### Rule 1  
  
```  
IF ItemA.Id == 1 and ItemA.Value != 20  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 Adding the check on **ItemA.Value** prevents Rule 1 from evaluating to **true** again after the actions of Rule 1 are executed the first time.  
  
## Using Update function on XML facts  
 Take the two rules that follow as an example. Suppose that. Rule 1 evaluates the total count of the items in a purchase order message, and rule2 sets the status to "Needs approval" if the total count is greater than or equal to 10.  
  
### Rule 1  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count)  
```  
  
### Rule 2  
  
```  
IF ProcessPO.Order:/Order/Items/TotalCount >= 10  
THEN ProcessPO.Order:/Order/Status = "Needs approval"  
```  
  
 If you pass the following purchase order (PO) message as an input to this policy, you notice that the status is not set to "Needs approval" even though the total item count is 14. It is because that the rule2 is evaluated only at the beginning when the value of the **TotalCount** field is 0, and the rule is not evaluated each time the total available count is updated. To have the conditions reevaluated each time the **TotalCount** is updated, you need to call the **Update** function on the parent node (**Items**) of the modified node (**TotalCount**). If you change the Rule1 as shown below, and test it one more time, you should see the value of the Status field set to "Needs Approval".  
  
```  
<ns0:Order xmlns:ns0="http://ProcessPO.Order">  
    <Items>  
        <Item>  
            <Id>ITM1</Id>  
            <Count>2</Count>  
        </Item>  
        <Item>  
            <Id>ITM2</Id>  
            <Count>5</Count>  
        </Item>  
        <Item>  
            <Id>ITM3</Id>  
            <Count>7</Count>  
        </Item>  
        <TotalCount>0</TotalCount>  
    </Items>  
    <Status>No approval needed</Status>  
</ns0:Order>  
```  
  
 The modified **Rule 1** is as follows:  
  
### Rule 1  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count) AND  
Update(ProcessPO.Order:/Order/Items)  
```  
  
## Using Update function on database facts  
  
### TypedDataTable  
 If **Update** is called on a **TypedDataTable**, **Update** is called by the engine on all associated **TypedDataRows**. **Update** may also be called on individual **TypedDataRows**.  
  
### DataConnection  
 Update of a **DataConnection** is not supported. Use **Assert** instead.  
  
## See Also  
 [Engine Control Functions](../core/engine-control-functions.md)