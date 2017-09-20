---
title: "Assert | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert function [Business Rules Engine], .NET objects"
  - "Assert function [Business Rules Engine], TypedXMLDocument"
  - "Assert function [Business Rules Engine]"
  - "Assert function [Business Rules Engine], examples"
  - "Assert function [Business Rules Engine], TypedData table"
  - "Assert function [Business Rules Engine], DataConnection"
  - ".NET objects"
ms.assetid: e9989214-3c10-4691-9c38-f6fe64e511ed
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Assert
*Assertion* is the process of adding object instances into the Business Rule engine's working memory. The engine processes each instance according to the conditions and actions that are written against the type of the instance, using the match-conflict resolution-action phases.  
  
 The following topics describe behaviors that result from using the **Assert** function for different fact types.  
  
## .NET Objects  
 Each object is asserted into the working memory as a separate instance. This means that the instance is analyzed by each predicate that references the object's type (for example, IF Object.Property = 1). It is also made available to rule actions that reference the type, dependent on the results of the rule conditions.  
  
 Consider the following example.  
  
 **Rule 1**  
  
```  
IF A.Value = 1  
THEN A.Status = "good"  
```  
  
 **Rule 2**  
  
```  
IF B.Value = 1  
THEN A.Status = "good"  
```  
  
 In Rule 1, only those instances of A that have a Value of 1 will have their **Status** property updated. In Rule 2, however, if the condition evaluates to **true**, all instances of A will have their status updated. In fact, if there are multiple instances of B, the A instances will be updated each time the condition evaluates to **true** for a B instance.  
  
 To assert a .NET object from within a rule, you can add the built-in **Assert** function as a rule action. Note that the rule engine has a **CreateObject** function, but it is not displayed as a separate function in the Business Rule Composer. Its invocation is built by dragging the constructor method of the object you wish to create from the .NET Class view of the Facts Explorer to the action pane. The Business Rule Composer then translates the constructor method into a **CreateObject** call in the rule definition.  
  
## TypedXmlDocument  
 When a **TypedXmlDocument** is asserted, the Business Rule Engine creates child **TypedXmlDocument** instances based on the selectors defined in the rule.  
  
 Selectors and fields are both XPath expressions. You can think of selectors as a way to isolate nodes of an XML document, and fields as identifying specific items within the selector. All the fields inside one selector are grouped together as an object by the engine. When you select a node under the **XML Schemas** tab in the Facts Explorer, the Business Rule Composer automatically fills in the **XPath Selector** property for all nodes, and the **XPath Field** property for any node that does not contain child nodes. Alternatively, you can enter your own XPath expressions for **XPath Selector** and **XPath Field** if necessary.  
  
 If the selector matches multiple portions of the XML document, multiple objects of this type are asserted into or retracted from the rule engine working memory. Assume you have the following XML.  
  
```  
<root>  
   <order customer="Joe">  
      <item name="router" quantity="10" cost="550" />  
      <item name="switch" quantity="3" cost="300" />  
   </order>  
   <order customer="Jane">  
      <item name="switch" quantity="1" cost="300" />  
      <item name="cable" quantity="23" cost="9.99" />  
   </order>  
</root>  
```  
  
 If you use the selector /root/order (or //order), two objects are added to the working memory.  
  
 1\)  
  
```  
<order customer="Joe">  
   <item name="router" quantity="10" cost="550" />  
   <item name="switch" quantity="3" cost="300" />  
</order>  
```  
  
 2\)  
  
```  
<order customer="Jane">  
   <item name="switch" quantity="1" cost="300" />  
   <item name="cable" quantity="23" cost="9.99" />  
</order>  
```  
  
 Within each selector, the individual fields are referred to by XPaths.  
  
 If you use the selector /root/order/item (or (//order/item or //item), four objects  are added to the rule engine working memory, the two items for Joe and the two items for Jane.  
  
```  
<root>  
   <order customer="Joe">  
  
   </order>  
   <order customer="Jane">  
  
   </order>  
</root>  
```  
  
 Each object has access to three fields—@name, @quantity, and @cost. Because the object is a reference into the original document, you can refer to parent fields (for example, "../@customer").  
  
 You can use multiple selectors within the same document. This enables you to view different parts of the document (for example, if one section is the order and another section contains the shipping address). However, keep in mind that the objects that are created are defined by the XPath string that created them. Using a different XPath expression, even if it resolves to the same node, results in a unique **TypedXmlDocument**.  
  
 The rule engine supports basic .NET scalar types natively, as well as objects for reference types. XML documents are basically text, but based on the type that was specified when the rule was built, the field value may be of any type. Also, because fields are XPath expressions, they may return a nodeset, in which case the first item in the set is used as the value.  
  
 Behind the scenes, the rule engine can convert a text field value to any one of the supported types through the **XmlConvert** function. You can specify this by setting the type in the Business Rule Composer. An exception is thrown if a conversion is not possible. The types **bool** and **double** can be retrieved only as their respective type, strings, or objects.  
  
## TypedDataTable  
 When a **TypedDataTable** is asserted, all **DataRows** contained in the **DataTable** are automatically asserted into the engine as **TypedDataRows**. Any time a table or table column is used as a rule argument, the expression is evaluated against the individual **TypedDataRows**, and not against the **TypedDataTable**.  
  
 For example, suppose that you have the following rule built against a "Customers" table:  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
> [!NOTE]
>  To build a rule against a database table, you must use **Data table / row** as the database binding type.  
  
 Suppose that you assert the following **DataTable** with three **DataRows** into the engine (as a **TypedDataTable**).  
  
|CustomerID|ContactTitle|  
|----------------|------------------|  
|001|Supply Clerk|  
|002|Supply Clerk|  
|003|Supply Clerk|  
  
 The engine inserts three **TypedDataRows**: 001, 002, and 003.  
  
 Each **TypedDataRow** is evaluated independently against the rule. The first **TypedDataRow** meets the rule condition and the second two fail. The results appear as follows.  
  
|CustomerID|ContactTitle|  
|----------------|------------------|  
|001|Purchasing Manager|  
|002|Supply Clerk|  
|003|Supply Clerk|  
  
> [!NOTE]
>  TypedDataRows can also be directly asserted into the engine. These are processed in the same way as described earlier.  
  
 The **DataSetName.DataTableName** is considered to be a unique identifier. Therefore, if a second **TypedDataTable** is asserted with the same **DataSet** name and **DataTable** name, it supersedes the first **TypedDataTable**. All **TypedDataRow**s associated with the first **TypedDataTable** are retracted, and the second **TypedDataTable** is asserted.  
  
## DataConnection  
 As with a **TypedDataTable**, dragging a table or column as a rule argument in the Business Rule Composer results in rules built against the returned **TypedDataRow**s as opposed to the **DataConnection** itself.  
  
 Suppose that the following rule is created and a **DataConnection** is asserted that contains a **SqlConnection** to Northwind.Customers:  
  
```  
IF Northwind.Customers.CustomerID = 001  
THEN Northwind.Customers.ContactTitle = "Purchasing Manager"  
```  
  
 When the engine evaluates the rule used in the **TypedDataTable** section, it dynamically builds a query that looks like:  
  
```  
SELECT *  
FROM Northwind.Customers  
WHERE CustomerID = 1  
```  
  
 Because only one row in the database meets this criterion, only one **TypedDataRow** is created and asserted into the engine for further processing.  
  
## Summary of Asserted Entities and Instance Types  
 The following table summarizes the assert behavior for the various types, showing the number of resulting instances created in the engine for each asserted entity, as well as the type that is applied to each of those instances to identify them.  
  
|Entity|Number of instances asserted|Instance type|  
|------------|----------------------------------|-------------------|  
|.NET object|1 (the object itself)|Fully Qualified .NET Class|  
|TypedXmlDocument|1-N TypedXmlDocument(s): Based on Selector bindings created and document content|DocumentType.Selector|  
|TypedDataTable|1-N TypedDataRow(s):<br /><br /> One for each DataRow in the DataTable|DataSetName.DataTableName|  
|TypedDataRow|1 (the TypedDataRow asserted)|DataSetName.DataTableName|  
|DataConnection|1-N (one for each TypedDataRow returned by querying the DataConnection)|DataSetName.DataTableName|  
  
## See Also  
 [Engine Control Functions](../core/engine-control-functions.md)