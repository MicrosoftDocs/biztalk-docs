---
description: "Learn more about: Using DataConnection and TypedDataTable"
title: "Using DataConnection and TypedDataTable"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Using DataConnection and TypedDataTable
In many scenarios, using **DataConnection** provides better performance and consumes less memory than using **TypedDataTable**. However, **TypedDataTable** may be required in some cases because of certain restrictions on using **DataConnection**. In some other cases, using **TypedDataTable** may yield better performance than using **DataConnection**. This topic describes the criteria and factors that you should consider for choosing the right approach.  
  
## When to use TypedDataTable instead of DataConnection  
 Use TypedDataTable instead of DataConnection in the following instances:  
  
-   Data changes need to be made but the table does not have a primary key. To make data changes by using **DataConnection**, a primary key is required. Therefore, if there is no primary key, **TypedDataTable** is the only viable approach.  
  
    > [!NOTE]
    >  The rule engine only updates the values in memory for a **TypedDataTable**. It is up to the caller to make those changes permanent.  
  
-   Selectivity is high, which means that a large percentage of rows in the table will pass the tests specified as rule conditions. In this case, **DataConnection** does not provide much benefit and it may perform worse than **TypedDataTable**.  
  
-   The table is small, typically, a table that contains fewer than 500 rows. Note that this number could be larger or smaller depending on the rule shape and the memory available to the rule engine.  
  
-   Rule-chaining behavior is expected in a rule set. Calling the **Update** function on a **DataConnection** is not supported, but you could invoke **DataConnection.Update** in a rule using a helper method. When rule chaining is required, **TypedDataTable** is a better choice.  
  
-   One or more columns in the table hold a very large amount of data that is not required by the rules. An example is an image database, where the columns hold the image (large amount of data), name, date, and so on. If the image is not required, it may be better to select only the columns needed by the rules. For example, issuing a query such as "SELECT Name, Date from TABLE" can be more efficient than using **DataConnection**.  
  
-   If many rules need or update the same database row, using a **TypedDataTable**, the row is shared between all rules, and if the condition is the same (for example, Table.Column == 5), the condition evaluation can be optimized. With a **DataConnection**, in general, a query is generated for each rule that uses the **DataConnection**. Although the rows are reused (if the table has a primary key), multiple queries could be generated to get the same data each time.  
  
## When to use DataConnection instead of TypedDataTable  
 Use DataConnection instead of TypedDataTable in the following instances:  
  
-   The table contains a large number of rows, but selectivity is low—only a small percentage of rows will satisfy the rule conditions.  
  
-   Only one database table is large; all other objects used in the rule have a small number of instances. In the worst case, the number of queries executed against the database is equal to the product of all the other instances used in the rule.  
  
-   Rules consist exclusively of conjunctive conditions and objects other than database table are used in these rules.  
  
## See Also  
 [Data Access in the Business Rule Engine](../core/data-access-in-the-business-rule-engine.md)
