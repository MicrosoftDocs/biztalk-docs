---
title: "Custom Date-Time Formats | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5efbec4-3138-44d7-bc76-f9c21547e1d5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Custom Date-Time Formats

## Overview
Due to their legacy origins, the flat file formats for which you create flat file schemas are bound to use date and time formats that do not conform to ISO 8601 formats. Therefore, when you are creating a flat file schema and you set the **Data Type** property of a **Field Element** or **Field Attribute** node to one of the XML Schema definition (XSD) language primitive data types, **xs:dateTime**, **xs:time**, or **xs:date**, you can use the **Custom Date/Time Format** property to specify an alternative format for date or time values.  

> [!NOTE]
>  Storage in the message box truncates time values in **xs:dateTime** and **xs:time** elements below the millisecond level. A similar loss of precision may occur when converting to .NET date/time data types.  

 When the flat file disassembler translates such a field to its equivalent XML format, the value of the **Custom Date/Time Format** property will be used to allow the flat file date/time format to be converted to its ISO 8601 compliant equivalent. Likewise, when the flat file assembler translates an ISO 8601 compliant date/time value to its flat file equivalent, the format string specified in the **Custom Date/Time Format** property will be used construct the appropriate date/time format expected in the flat file.  

> [!NOTE]
>  By default, values that correspond to XSD date and time data types, of which there are several, must conform to ISO 8601 formats. In brief, dates are expressed as **YYYY-MM-DD** and hours are expressed as **hh:mm:ss** using 24-hour notation. When they occur together, date and time values are separated by the "T" character: **YYYY:MM:DDThh:mm:ss**.  

 You can configure the **Custom Date/Time Format** property with almost any time and date format, except for Julian dates. The drop-down list provides various choices, but you can also type a different format of your choosing. The date and time formats use the Common Language Runtime (CLR) **DateTime** facilities. The exception is that a single character d, m, or M is automatically prepended with a percent sign (%) to yield the corresponding single element of the DateTime value. The allowable separators for custom date/time formats are dash (-), slash (/), and period (.). For more information about **DateTime** formats, search on "DateTimeFormatInfo" in the Visual Studio document collection.  

## See Also  
- [Field Considerations](../core/field-considerations.md)   
- **Data Type (Node Property of All Schemas)** and **Custom Date-Time Format (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
