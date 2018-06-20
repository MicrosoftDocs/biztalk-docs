---
title: "Functoid Categories | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 029905e2-f01a-436a-b2ed-a364379c9cc5
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Functoid Categories
BizTalk functoids are divided into categories according to their intended use. For example, database functoids are designed for extracting data from a database at run time, mathematical functoids are used to perform mathematical operations, and so on. In BizTalk Mapper, functoids appear by category in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox. 

## Categories & description
The following table shows the functoid categories, briefly describes the category, and shows the list of functoids in each category, including links to their corresponding reference pages.  
  
|Functoid category <br/><br/> Category description|Functoids in category|  
|---|---|  
|**Advanced** <br /><br /> Primarily used with looping records. Also used for running arbitrary script or compiled code.|Assert, Index, Iteration, Looping, Mass Copy, Nil Value, Record Count, Scripting, Table Extractor, Table Looping, Value Mapping, Value Mapping (Flattening)|  
|**Conversion** <br /><br /> Used to convert to and from ASCII, and between numeric bases.|ASCII to Character, Character to ASCII, Hexadecimal, Octal|  
|**Cumulative** <br /><br /> Used to perform mathematical operations in looping records, such as averages and concatenation.|Cumulative Average, Cumulative Concatenate,  Cumulative Maximum, Cumulative Minimum, Cumulative Sum|  
|**Database** <br /><br /> Used to extract data from a database and use it in destination instance messages.|Database Lookup, Error Return, Format Message, Get Application ID, Get Application Value, Get Common ID, Get Common Value, Remove Application ID, Set Common ID, Value Extractor|  
|**Date and Time** <br /><br /> Used to retrieve the current date and time, and to calculate delta times.|Add Days, Date, Date and Time, Time|  
|**Logical** <br /><br /> Used to perform a variety of logical operations, such as greater than and logical existence.|Equal, Greater Than, Greater Than or Equal To, IsNil, Less Than, Less Than or Equal To, Logical AND, Logical Date, Logical Existence, Logical Numeric, Logical NOT, Logical OR, Logical String, Not Equal|  
|**Mathematical** <br /><br /> Used to perform a variety of mathematical operations, such as addition and multiplication.|Absolute Value, Addition, Division, Integer, Maximum Value, Minimum Value, Modulo, Multiplication, Round, Square Root, Subtraction|  
|**Scientific** <br /><br /> Used to perform a variety of scientific operations, such as logarithms and trigonometry.|10^n, Arc Tangent, Base-Specified Logarithm, Common Logarithm, Cosine, Natural Exponential Function, Natural Logarithm, Sine, Tangent, X^Y|  
|**String** <br /><br /> Used to perform a variety of string functions, such as trimming and concatenation.|Lowercase, Size, String Concatenate, String Extract, String Find, String Left, String Left Trim, String Right, String Right Trim, Uppercase|  
  
> [!NOTE]
>  The purpose of a functoid is usually obvious from its name.  
> 
> [!NOTE]
>  All functoids included with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are inline C#, except for the **Database** functoids.  
  
## See Also  
 [Basic Functoids](../core/basic-functoids.md)   
 [Advanced Functoids](../core/advanced-functoids.md)