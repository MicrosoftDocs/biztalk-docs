---
description: "Learn more about: How to Handle Null and DBNull"
title: "How to Handle Null and DBNull"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Handle Null and DBNull
This topic describes the expected behaviors when dealing with null values associated with different types, and discusses options for checking null or existence of a particular field or member.  
  
## XML  
 The following applies to XML:  
  
-   An XML value will never be returned from a document as null. It is either an empty string or a "does not exist" error. When it is an empty string, an error may occur for conversion of certain types, for example, fields specified as an integer type when building rules.  
  
-   The Business Rule Composer does not allow you to set a field to null or to set the type of a field to **object**.  
  
-   Through the object model you can set the type to **Object**. In this case, the value returned is the type to which the XPath evaluates— **float**, **boolean**, or **string**, depending on the XPath expression.  
  
## .NET classes  
 The following applies to .NET classes:  
  
-   You are not allowed to compare to null if your return type is not an **object** type.  
  
-   You can pass null as a parameter for parameters that are not value types, but you may get a runtime error, depending on the implementation of the member.  
  
-   You can set fields of types derived from **Object** to null.  
  
## Data connection  
 The following applies to a data connection:  
  
-   You can compare any database table column to null, if the table allows nulls for the column and the column type is not **text**, **ntext**, and **image**.  
  
    > [!NOTE]
    >  The Business Rule Composer allows you to use columns of type, **text** and **ntext**, in conditions. However, when you execute the policy, you will receive an error message, which says, "The text, ntext, and image data types cannot be compared or sorted, except when using IS NULL or LIKE operator".  
  
-   You can set any database table column to null, if the table allows nulls for the column.  
  
-   The Business Rule Composer automatically sets the member type in the binding to **object**, if you compare or set to null for a value type; it changes back to the original type if you reset or replace the argument.  
  
-   For a string type, it changes the type to **object** if you set it to null, but leaves it as a string if you compare against null.  
  
-   You cannot compare or set to **DBNull.Value** from the Business Rule Composer, because it will not change the column type to **object**.  
  
-   The engine will convert a DBNull value to null for comparison and will convert null to a DBNull value for insertion into the database.  
  
-   Tests will ignore null values (this is the way SQL Server works). For example, if you have the rule "IF db.column > 5 THEN .", only the rows that have a value in db.column are tested—rows with null are skipped.  
  
## TypedDataTable and TypedDataRow  
 The following applies to TypedDataTable and TypedDataRow:  
  
-   The Business Rule Composer changes the field type to **object** in the same manner as with **DataConnection**s.  
  
-   Tests will fail for null values, unless you are comparing to null. For example, there will be an error in the rule "IF db.column > 5 THEN ", if any row asserted has a null value.  
  
     Note that because conditions are evaluated in parallel, tests like "IF db.column != NULL AND db.column > 5 THEN  " will still fail, because both tests are potentially evaluated on every row.  
  
## Checking for null or existence  
 When writing business rules, it is natural to check for the existence of a field before comparing its value. However, if the field is null or does not exist, comparing the value will cause an error. Assume you have the following rule:  
  
 IF Product/Quantity Exists AND Product/Quantity > 1  
  
 An error will be thrown in the rule if Product/Quantity does not exist. One of the ways to circumvent this problem is to pass a parent node to a helper method that returns the element value if it exists or something else if it does not. See the following rules.  
  
 **Rule 1**  
  
 IF EXISTS(Product/Quantity) THEN ASSERT(CREATEOBJECT(typeof(Helper), Product/Quantity)  
  
 **Rule 2**  
  
 IF Helper.Value == X THEN...  
  
 Another possible solution is to create a rule like the following:  
  
 IF Product/Quantity Exist Then CheckQuantityAndDoSomething(Product/Quantity)  
  
 In the preceding example, the CheckQuantityAndDoSomething function will check the parameter value and execute if the condition is met.  
  
> [!NOTE]
>  Alternatively, you can modify the XPath **Field** property for the XML fact to catch any errors, but it is not the recommended approach.
