---
title: "How to Analyze Multiple Objects of the Same Type in a Business Rule | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business rules, multiple types"
  - "Business Rules Framework, programming"
ms.assetid: ff9790c1-13b0-4eee-8cac-d4f25ef5f0b7
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Analyze Multiple Objects of the Same Type in a Business Rule
In many scenarios, you will write a business rule against a type and expect each instance of the type that is asserted into the engine to be separately analyzed and acted upon by the rule. In some scenarios, however, you will want to analyze multiple instances of a given type simultaneously in a rule.  
  
 Take for example a rule that uses instances of the **FamilyMember** class.  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember.Role == Son  
AND FamilyMember.Surname == FamilyMember.Surname  
THEN FamilyMember.AddChild(FamilyMember)  
```  
  
 The rule identifies a **FamilyMember** instance that is a **Father** and another instance that is a **Son**. If the instances are related by surname, the **Son** instance is added to a collection of children on the Father instance. If each **FamilyMember** instance were analyzed separately in the rule, the rule would never fire, because in this scenario, the **FamilyMember** only has one role—**Father** or **Son**.  
  
 Therefore, you must indicate to the engine that multiple instances should be analyzed together in the rule, and you need a way to differentiate the identity of each instance in the rule. The **Instance ID** property is used to provide this functionality. This field is available in the Properties window when a fact is selected in Facts Explorer. You should change the value of the field prior to dragging a fact or member into a rule.  
  
 Using the **Instance ID** property, the rule would be rebuilt. For those rule arguments that use the **Son** instance of **FamilyMember**, the **Instance ID** field is changed from the default of 0 to 1. When the Instance ID is changed from 0 and the fact or member is dragged into the rule editor, the value of Instance ID will show up in the rule after the class.  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember(1).Role== Son  
AND FamilyMember.Surname == FamilyMember(1).Surname  
THEN FamilyMember.AddChild(FamilyMember(1))  
```  
  
 Now, assume that a **Father** instance and a **Son** instance are asserted into the engine. The engine will evaluate the rule against the various combinations of the instances. Assuming that the **Father** and **Son** instance have the same surname, the **Son** instance will be added to the **Father** instance as intended.  
  
> [!NOTE]
>  The **Instance ID** is only used within the context of a given rule evaluation. It is not affixed to an object instance across the policy execution and is not related to the order in which objects are asserted. Each object instance will be evaluated in all rule arguments for that type.