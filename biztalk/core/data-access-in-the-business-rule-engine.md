---
title: "Data Access in the Business Rule Engine | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Business Rules Engine, data access"
  - "Business Rules Engine, helper classes"
  - "data, data access"
ms.assetid: 38da32af-1e0d-43fb-b946-fb49a11f1681
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Access in the Business Rule Engine
The rule engine supports only .NET objects natively. To handle data from a database, you can use the ADO.NET objects directly, but the engine provides some helper classes to simplify the use of database data from rules. The rule engine extends its support by exposing three database-related types: **TypedDataRow**, **TypedDataTable**, and **DataConnection**. This section describes these helper classes, gives recommendations about when to use each type, and discusses some performance implications when using them.  
  
 The helper classes are as follows:  
  
-   **TypedDataRow.** Constructed by using a reference to an ADO.NET **DataRow** instance. The **TypedDataRow** is an obvious choice for rules that only deal with data from one or a small number of rows from a particular table.  
  
-   **TypedDataTable.** Literally a collection of **TypedDataRow** objects. Each row in the database table will be wrapped as a **TypedDataRow** and asserted into the working memory by the rule engine.  
  
     A **TypedDataTable** requires an in-memory ADO.NET **DataTable**, which can be a performance overhead if this particular **DataTable** contains a very large number of rows. If a small number of rows in the database table is relevant and you can determine these rows prior to calling the rules, use a **DataTable**, otherwise use **TypedDataRow**.The assumption is that a high number of rows in the DataTable are relevant to the rules.  
  
-   **DataConnection.** Represents a table in a database accessed through a database connection. The difference between **DataConnection** and **TypedDataTable** is that in addition to the dataset name and table name, **DataConnection** requires a usable database connection and optionally a database transaction context.  
  
     Some or all predicates used in rules with the **DataConnection** will become part of query constraints against the database connection. Only rows that satisfy the query constraints will be retrieved from the database and used by the engine. This mechanism provides better performance and consumes less memory than holding a very large **DataTable** in memory.  
  
## In This Section  
  
-   [Considerations When Using DataConnection](../core/considerations-when-using-dataconnection.md)  
  
-   [Using DataConnection and TypedDataTable](../core/using-dataconnection-and-typeddatatable.md)