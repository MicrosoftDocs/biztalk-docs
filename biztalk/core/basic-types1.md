---
description: "Learn more about: Basic Types"
title: "Basic Types1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JD Edwards OneWorld adapters, data types"
  - "JD Edwards OneWorld adapters, business functions"
  - ".NET Framework, mapping [JD Edwards OneWorld adapters]"
  - "adapters [JD Edwards OneWorld adapters], data types"
  - "adapters [JD Edwards OneWorld adapters], .NET Framework"
  - "JD Edwards OneWorld adapters, .NET Framework"
  - "adapters [JD Edwards OneWorld adapters], business functions"
ms.assetid: d306ea1b-fb74-4fa3-9681-405252928df1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Basic Types
Microsoft BizTalk Adapter for JD Edwards OneWorld provides access only to JD Edwards OneWorld business functions. Business function metadata is read using a business function interface and used to find a list of business functions and associated data structures. Metadata is strongly typed in all cases for all business function methods.  
  
 All business function methods have the same calling convention: three parameters that are system derived, and a pointer to a data structure. The following table shows how the business function data types are represented.  
  
 **Business function data types**  
  
|JD Edwards OneWorld Data Type|Description|WDSL Conversion|  
|-----------------------------------|-----------------|---------------------|  
|char|Character string.|xsd:string of 1|  
|int|Short integer.|xsd:short|  
|long|Long integer.|xsd:short|  
|String|See [Handling String Values](../core/handling-string-values1.md).|xsd:string|  
|JDEDATE|Special implementation of dates.|xsd:date|  
|MATH_NUMERIC|Special implementation of floating point numbers, including currency values.|xsd:string of 32|  
|Byte|Single unsigned character.|xsd:string of 1|  
  
 The following table contains the list of basic types in JD Edwards OneWorld and how they map to the Microsoft .NET Framework.  
  
 **Basic types and how they map to the Microsoft .NET Framework**  
  
|JD Edwards OneWorld XE|.NET Framework|  
|----------------------------|--------------------|  
|char|String|  
|int|Short|  
|long|Short|  
|String|String|  
|JDEDATE|System.DateTime|  
|MATH_NUMERIC|String|  
|Byte|String|  
  
> [!NOTE]
>  If there is only one argument, and the return argument is void, the holder is replaced by the class, and the out portion becomes the return value. For example:  
  
```  
org.apache.axis.holders.DateHolder becomes a java.util.Date.   
```  
  
 The following is an example of method signatures:  
  
```  
void testDate1(org.apache.axis.holders.DateHolder date1  
        org.apache.axis.holders.DateHolder date2);  
  
java.util.Date testDate2(java.util.Date date);  
```  
  
## Character-Limited Strings  
 In JD Edwards OneWorld, some strings are character-limited. Any extra character causes an error. To see the limit of characters in the strings, you can use the Microsoft Adapter Wizard.  
  
## See Also  
 [Using the MATH_NUMERIC Type](../core/using-the-math-numeric-type2.md)   
 [Handling String Values](../core/handling-string-values1.md)   
 [Appendix A: Data Types](../core/appendix-a-data-types.md)
