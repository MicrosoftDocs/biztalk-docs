---
title: "Converting Data Types from Automation to RPG1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9db5f8ef-a636-4079-9299-bd31f744afbf
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Converting Data Types from Automation to RPG
Use the following table as a guide when you specify the way you want Transaction Integrator (TI) to handle conversions from Automation data types to Report Program Generator (RPG) data types.  
  
|TI Project default|RPG data type|Spec-ification|Field length|Field length meaning|Decimal places|  
|------------------------|-------------------|---------------------|------------------|--------------------------|--------------------|  
|Boolean (default)|Integer|I|5|digits|Blank|  
|Boolean|Integer|I|10|digits|Blank|  
|Boolean|Packed|P|3|digits|Blank,0|  
|Byte (default)|Character|A|1|bytes|Blank|  
|Byte|Unsigned|U|3-9|digits|Blank|  
|Byte|Packed|P|3|digits|Blank,0|  
|Byte|Integer|I|3-9|digits|Blank|  
|Currency (default)|Packed|P|1-30|digits|Blank,0-4|  
|Currency|Zoned|S|1-30|bytes|Blank,0-4|  
|Currency|Binary|B|1-4|digits|Blank,0-4|  
|Currency|Binary|B|5-9|digits|Blank,0-4|  
|Date (Date)|*MDY|None|8|bytes|Blank|  
|Date (Date)|*DMY|None|8|bytes|Blank|  
|Date (Date)|*YMD|None|8|bytes|Blank|  
|Date (Date)|*JUL|None|6|bytes|Blank|  
|Date (Date)|*ISO|None|10|bytes|Blank|  
|Date (Date)|*USA|None|10|bytes|Blank|  
|Date (Date)|*EUR|None|10|bytes|Blank|  
|Date (Date)|*JIS|None|10|bytes|Blank|  
|Date (Time)|*HMS|None|8|bytes|Blank|  
|Date (Time)|*ISO|None|8|bytes|Blank|  
|Date (Time)|*USA|None|8|bytes|Blank|  
|Date (Time)|*EUR|None|8|bytes|Blank|  
Date (Time)|*JIS|None|8|bytes|Blank|  
|Date|Timestamp|Z|Number?|bytes|Blank|  
|Decimal|Float|F|4|Bytes|Blank|  
|Decimal|Float|F|8|Bytes|Blank|  
|Decimal (default)|Packed|P|1-30|digits|Blank,0-30|  
|Decimal|Zoned|S|1-30|bytes|Blank,0-30|  
|Decimal|Binary|B|1-4|digits|Blank,0-4|  
|Decimal|Binary|B|5-9|digits|Blank,0-9|  
|Double (default)|Float|F|8|bytes|Blank|  
|Double [1]|Packed|P|1-30|digits|Blank,0-30|  
|Double [1]|Zoned|S|1-30|bytes|Blank,0-30|  
|Double|Binary|B|1-4|digits|Blank,0-4|  
|Double|Binary|B|5-9|digits|Blank,0-9|  
|Integer (default)|Integer|I|1-5|digits|Blank|  
|Integer|Packed|P|1-30|digits|Blank,0|  
|Integer|Zoned|S|1-30|bytes|Blank,0|  
|Integer|Binary|B|1-5|digits|Blank,0|  
|Long (default)|Integer|I|1-9|digits|Blank|  
|Long|Packed|P|1-30|digits|Blank,0|  
|Long|Zoned|S|1-30|bytes|Blank,0|  
|Long|Binary|B|1-9|digits|Blank,0|  
|Single (default)|Float|F|4|bytes|Blank|  
|Single [1]|Packed|P|1-30|digits|Blank,0-30|  
|Single [1]|Zoned|S|1-30|bytes|Blank,0-30|  
|Single|Binary|B|1-9|digits|Blank,0-9|  
String (default)|Character|A|1-32755|Bytes==Char|Blank|  
|String|Graphic|G|1-16371|Char|Blank|  
  
> [!NOTE]
>  Note [1] in the preceding table indicates that when you convert whole or fractional numbers from Visual Basic Single or Visual Basic Double data types to Packed Decimal or distributed program call (DPC) Zoned Decimal data types, TI is limited to a precision from 1 through 18 digits to the left of the decimal point (for example, 1.2345678901234567E+17).  
  
> [!NOTE]
>  While TI left-justifies all strings, the RPG MOVE command right-justifies all strings. If you are programming an RPG application, use the MOVEL or EVAL commands to perform the equivalent operation in RPG while manipulating a string. **See Also**  
  
 [Supported TI Data Types](../core/supported-ti-data-types2.md)  
  
 [Converting Data Types from RPG to Automation](../core/converting-data-types-from-rpg-to-automation1.md)  
  
 [Data Type Conversion](../core/data-type-conversion1.md)