---
description: "Learn about the basic data types used by the business function interface methods in Microsoft BizTalk Adapter for JD Edwards EnterpriseOne that provide exclusive access to JD Edwards EnterpriseOne business functions."
title: "Basic Types2"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Basic Types

Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides access only to JD Edwards EnterpriseOne business functions. Business function metadata is read using a business function interface and used to find a list of business functions and associated data structures. Metadata is strongly typed in all cases for all business function methods.  
  
 All business function methods have the same calling convention: three parameters that are system derived, and a pointer to a data structure. The following table shows how business function data types are represented.  
  
|JD Edwards EnterpriseOne Data Type|Description|WDSL Conversion|  
|----------------------------------------|-----------------|---------------------|  
|char|Character string.|xsd:string of 1|  
|int|Short integer.|xsd:short|  
|long|Long integer.|xsd:short|  
|String|See [Handling String Values](../core/handling-string-values2.md).|xsd:string|  
|JDEDATE|Special implementation of dates.|xsd:date|  
|MATH_NUMERIC|Special implementation of floating point numbers, including currency values.|xsd:string of 32|  
|Byte|Single unsigned character.|xsd:string of 1|  
|JDEUTIME|Includes both date and time components.<br /><br /> The data type stores all dates/times and performs all date/time calculations in Coordinated Universal Time (UTC).|xsd:dateTime|  
  
## See Also  
 [Using the MATH_NUMERIC Type](../core/using-the-math-numeric-type1.md)   
 [Handling String Values](../core/handling-string-values2.md)   
 [Appendix B: Data Types](../core/appendix-b-data-types.md)
