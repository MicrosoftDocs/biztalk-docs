---
title: "Syntax for a SELECT Statement in Siebel | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Data Provider for Siebel, searching and sorting data using"
  - "Data Provider for Siebel, SELECT statement"
  - "SELECT statement, syntax for"
ms.assetid: 8528b115-d6f3-420d-8617-0e56dc8922bf
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Syntax for a SELECT Statement in Siebel
Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ADO.NET clients can perform a SELECT query on Siebel business components by specifying a WHERE clause that represents a valid Siebel search specification. The syntax for the SELECT statement is:  
  
```  
SELECT  
<column name 1> AS <column alias 1>,  
<column name 2> AS <column alias 2>,  
…  
FROM  
<Business object name>.<Business component name> AS <table alias>  
WHERE  
<filter condition>  
OPTION  
'ViewMode <value>'  
```  
  
 In the above syntax, the ViewMode option corresponds to the Siebel system View Modes, which is a filtering mechanism to restrict the set of records that match the query. For the allowed set of values, see the Siebel documentation.  
  
> [!NOTE]
>  If the field names in the WHERE clause contain special characters or empty spaces, make sure you always enclose the field names within square brackets.  
> 
> [!NOTE]
>  In SELECT queries containing alias names with special characters, make sure you include the alias names within square brackets.  
> 
> [!NOTE]
>  The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports alias names for tables in the SELECT clause but not in the WHERE clause.  
  
## Searching and Sorting Data Using the Data Provider for Siebel  
 The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports a filter condition in SQL statements based on the search specifications supported by the Siebel system.  
  
 The rules for the search specification are:  
  
- Standard comparison operators must be used to compare a field to a constant, or one field to another field. These include =, !=, >, <, >=, and <=.  
  
  ```  
  Example: [Revenue] > 5000  
  ```  
  
- String constants must be enclosed in double quotation marks, and the string values must be case-sensitive.  
  
  ```  
  Example: [Type] != "COST LIST"  
  ```  
  
- The logical operators AND, OR, and NOT must be used to negate or combine expressions. Case sensitivity is ignored in these operators; for example, “and” is the same as “AND”.  
  
  ```  
  Example: [Competitor] IS NOT NULL and [Competitor] != "N"  
  ```  
  
- A field name in a search specification must be enclosed in square brackets.  
  
  ```  
  Example: [Conflict Id] = 0  
  ```  
  
- The LIKE operator may be used to create text string comparison expressions in which a field is compared to a constant, or a field to another field and a match on only the first several characters is required. The wildcard characters “*” and “?” must be used to indicate any number of characters, and a single character, respectively.  
  
- ADO.NET clients can specify original Siebel business objects, business components, and business component field names. These names must be enclosed in square brackets if they contain any special characters or white space. Examples of queries that are supported are:  
  
  ```  
  SELECT [Name], [Postal Code] FROM Account.Account where [Postal Code] != '11065'  
  SELECT [Name], [Postal Code], Id From Account.Account where [Postal Code] != '60626' Order BY Id ASC, Name DESC  
  SELECT * FROM [Admin Price List].[Price Book Items]  
  ```  
  
  The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports sort specifications in SQL statements based on the sort specification supported by Siebel. The rules for the sort specification are:  
  
- Use commas to separate field names in a sort specification; for instance, Name, Location  
  
- To indicate that a field in the list sorts in descending order, include (DESC) after the field name, as in “Start Date (DESC).” If no sort order is specified, ascending order is used. To explicitly specify ascending order, use the keyword (ASC).  
  
- The sort specification expression must be 255 characters or less.  
  
## See Also  
 [Use the .NET Framework Data Provider for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)