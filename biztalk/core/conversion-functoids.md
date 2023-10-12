---
description: "Learn more about: Conversion Functoids"
title: "Conversion Functoids"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Conversion Functoids

## Overview
**Conversion** functoids are used to convert between numbers and their ASCII equivalents, and to convert base 10 numbers to their base 8 and base 16 equivalents.  
  
 All of the conversion functoids take a single input parameter.  
  
> [!NOTE]
>  Due to changes in the underlying type system, the **Conversion** functoids in this version of BizTalk Mapper produce slightly different results than those produced in previous versions. For example, in previous versions of BizTalk Mapper an input value of -20 to the **Hexadecimal** functoid resulted in an output of 0xFFEC. In this version, the same input value of -20 will result in an output of 0xFFFFFFEC.  

## Available functoids  
 The **Conversion** functoids are: 

* ASCII to Character
* Character to ASCII
* Hexadecimal
* Octal

These functoids are described [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 

## See Also  
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
