---
description: "Learn more about: How to Return True or False from a Policy"
title: "How to Return True or False from a Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a7bb9b2-14aa-44e7-a290-e49bf53bc594
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Return True or False from a Policy
You cannot specify a return type for a policy directly. However, you can pass one of the following types of facts to the policy, have the policy change the value of the fact to `true` or `false`, and then check the value of the property/element/column after the policy is executed:  
  
-   A .NET object with a property of type `Boolean`  
  
-   An XML document with an element of type `Boolean`  
  
-   A database table with a column of type `Boolean`
