---
title: "Logical Functoids | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e37cdfc3-66de-4333-84eb-a8765afa8407
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Logical Functoids

## Overview
**Logical** functoids are used to perform the following types of operations:  

- Perform specific logical tests at run time. The **Logical OR**, **Logical NOT** and **Logical AND** functoids can be used to determine whether a record is created in a destination instance message, such as the following:  

   If ShipTo **OR** OrderedBy are present, create BillTo address record.  

   You can also use these functoids in conjunction with the **Looping** functoid to configure how many times a record loops.  

- Control whether a specific record is created in a destination instance message at run time. Functoids such as **IsNil**, **Logical Numeric**, **Less Than**, and **Greater Than** can be used to control whether a record is created.  

   If the result of one of these logical functoids is **True**, the corresponding record in the destination instance message is generated. If the result is **False**, the corresponding record in the destination instance message is not generated.  

  The functoids **IsNil**, **Logical Date**, **Logical Existence**, **Logical NOT**, **Logical Numeric**, and **Logical String** accept only one parameter. The functoids **Equal**, **Greater Than**, **Greater Than or Equal To**, **Less Than**, **Less Than or Equal To**, and **Not Equal** accept two input parameters. Whereas, the **Logical AND** and **Logical OR** functoids accept input parameters between 2 and 100.  

  The output of a **Logical** functoid can also be accepted as input to other functoids in a map. If both a **Logical** functoid and a looping functoid are linked together, and then linked to a record in the destination schema, the looping functoid is used only when the **Logical** functoid output is **True**.  

  You can also use **Logical** functoids with the **Value Mapping** or **Value Mapping (Flattening)** functoids to control whether a record in the destination instance message is created.  

> [!IMPORTANT]
>  If you link two records or fields in the source schema to two different **Logical** functoids, and then link each of the **Logical** functoids to the same record in the destination schema, only the first **Logical** functoid is used in the generated Extensible Stylesheet Language Transformations (XSLT). The second link, from the second **Logical** functoid, is ignored.  

> [!NOTE]
>  Logical functoids are case-sensitive when comparing two strings. For example, "Abc" and "abc" are not equal. The exception to this rule is when **Logical** functoids compare strings that represent the Boolean values **True** and **False**. For example, "True" and "true" are equal.  

## Available functoids  
 The **Logical** functoids are: 

* Equal
* Greater Than
* Greater Than or Equal To
* IsNil
* Less Than
* Less Than or Equal To
* Logical AND
* Logical Date
* Logical Existence
* Logical NOT
* Logical Numeric
* Logical OR
* Logical String
* Not Equal

More details on these functions are [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

## See Also  
- [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
- **Logical Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
