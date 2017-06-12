---
title: "Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "functoids, properties"
  - "maps, functoids"
  - "BizTalk Mapper, functoids"
  - "messages, functoids"
  - "messages, transforming schemas"
ms.assetid: ed56b236-3663-4a20-a2ea-14e4a4492bf8
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Functoid Reference
BizTalk Mapper provides an extensive set of functoids that can be used in maps to perform a variety of operations on data that is being transformed from a source instance message to a destination instance message. This section provides reference information about the BizTalk Mapper functoids.  
  
> [!IMPORTANT]
>  Because Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the underlying functionality of the .NET Framework, the results produced by some functoids vary from the equivalent functoids in previous versions of BizTalk Server. You should test your maps thoroughly to ensure you are getting the results you expect.  
  
> [!NOTE]
>  Whenever an input parameter to a functoid is not valid, a default value is passed to the functoid in its place. For numeric input parameters, the default value is zero (0). For all other input parameters, the default value is blank.  
>   
>  The above doesn’t apply to all the functoids. For instance, the default value is applied to functoids like MathAdd, but not applied to functoids like MathSqrt or GetCummulativeAvg.  
  
> [!NOTE]
>  If a functoid connects to a **Record** node in the destination schema, that node should have its **Mixed** property set to **True** for the output document to be valid against the schema. This is because the functoid writes data into the corresponding element. The **Mixed** property may be set to **False** if the **Content Type** is **SimpleContent**.  
  
 The following table shows the categories into which these functoids have been divided.  
  
|Functoid Category|Description|  
|-----------------------|-----------------|  
|[Advanced Functoids Reference](../core/advanced-functoids-reference.md)|Use **Advanced** functoids to create various types of data manipulation, such as implementing custom script, value mapping, and managing and extracting data from looping records.|  
|[Conversion Functoids Reference](../core/conversion-functoids-reference.md)|Use **Conversion** functoids to convert characters to and from their numeric representation, and to convert numbers from one base to another.|  
|[Cumulative Functoids Reference](../core/cumulative-functoids-reference.md)|Use **Cumulative** functoids to perform various types of accumulation operations for values that occur multiple times within an instance message.|  
|[Database Functoids Reference](../core/database-functoids-reference.md)|Use **Database** functoids to look up data from a database and to perform simple cross-referencing operations (sometimes called ID mapping).|  
|[Date and Time Functoids Reference](../core/date-and-time-functoids-reference.md)|Use **Date and Time** functoids to add date, time, date and time, or add days to a specified date, in output data.|  
|[Logical Functoids Reference](../core/logical-functoids-reference.md)|Use **Logical** functoids to conditionally control the behavior of other functoids and to determine whether particular output data is created.|  
|[Mathematical Functoids Reference](../core/mathematical-functoids-reference.md)|Use **Mathematical** functoids to perform specific numeric calculations such as addition, multiplication, and division.|  
|[Scientific Functoids Reference](../core/scientific-functoids-reference.md)|Use **Scientific** functoids to perform specific scientific calculations such as logarithmic, exponential, and trigonometric functions.|  
|[String Functoids Reference](../core/string-functoids-reference.md)|Use the **String** functoids to manipulate data strings by using well-known string functions such as concatenation, length, find, and trim.|