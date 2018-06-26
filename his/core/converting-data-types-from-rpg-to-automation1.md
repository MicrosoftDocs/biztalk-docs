---
title: "Converting Data Types from RPG to Automation1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4e3504d-2226-4de4-9dcb-4804df45bf12
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Converting Data Types from RPG to Automation
Use the following tables as a guide when you set up the way you want Transaction Integrator (TI) to handle conversions from report program generator (RPG) data types to Automation data types. For more information about the specific data types, see [Supported TI Data Types](../core/supported-ti-data-types2.md).  
  
 The following table describes the TI Project property abbreviations used in the data type tables that follow.  
  
|Abbreviation|Description|  
|------------------|-----------------|  
|t|Truncate|  
|e|Error|  
|r|Round|  
|sp|Space pad|  
|nt|Null terminate|  
|SO|Add leading shift in|  
|SI|Add trailing shift out|  
|PE|Pack even|  
|TIP|TI Project|  
  
 Pack even (PE) indicates that the definition specification uses the pack even option for RPG. PE indicates that the precision is an even number of digits when the From and To specification positions are used, which implies a byte count instead of a digit count and which might mean that the high-order digit position is ignored. For example, the following table shows how the number 256 in an RPG packed field is represented in internal memory.  
  
> [!NOTE]
>  For purposes of this example, the number 256 fits in 2 bytes of memory in both the PE and No PE option.  
  
| Packed data type option |              Byte 1               |              Byte 2              |
|-------------------------|-----------------------------------|----------------------------------|
|                         | High-order byte high-order nibble | High-order byte low-order nibble |
|          No PE          |                 2                 |                5                 |
|           PE            |              ignored              |                5                 |
  
|RPG data type|Spec-ification|RPG field length|TIP data type|TIP default error handling|TIP<br /><br /> default field length|TIP default decimals|TIP<br /><br /> default string<br /><br /> handling|  
|-------------------|---------------------|----------------------|-------------------|--------------------------------|----------------------------------|--------------------------|-----------------------------------------|  
|Character|A|1|Byte|None|None|None|None|  
|Character|A|1-32755|String|t,e|80|None|sp,nt|  
|Graphic|G|1-16371|String|t,e|80|None|sp|  
|Binary|B|1-4|Currency|t,r,e|4|2|None|  
|Binary|B|5-9|Currency|t,r,e|9|2|None|  
|Binary|B|1-4|Decimal|t,r,e|4|2|None|  
|Binary|B|5-9|Decimal|t,r,e|9|2|None|  
|Binary|B|1-4|Double|t,r,e|4|2|None|  
|Binary|B|5-9|Double|t,r,e|9|2|None|  
|Binary|B|1-5|Integer|t,r,e|4|None|None|  
|Binary|B|1-9|Long|t,r,e|9|None|None|  
|Binary|B|1-9|Single|t,r,e|4|2|None|  
|Integer|I|5|Boolean|None|None|None|None|  
|Integer|I|10|Boolean|None|None|None|None|  
|Integer|I|3-9|Byte|t,r,e|3|None|None|  
|Integer|I|1-5|Integer|t,r,e|4|None|None|  
|Integer|I|1-5|Long|t,r,e|9|None|None|  
|Packed|P|3|Boolean|None|None|None|None|  
|Packed|P|3|Byte|t,r,e,npe|3|None|None|  
|Packed|P|1-30|Currency|t,r,e|8|2|None|  
|Packed|P|1-30|Decimal|t,r,e|8|2|None|  
|Packed|P|1-30|Double|t,r,e|8|2|None|  
|Packed|P|1-30|Integer|t,r,e|3|None|None|  
|Packed|P|1-30|Long|t,r,e|5|None|None|  
|Packed|P|1-30|Single|t,r,e|8|2|None|  
|Zoned|S|1-30|Currency|t,r,e|15|2|None|  
|Zoned|S|1-30|Decimal|t,r,e|15|2|None|  
|Zoned|S|1-30|Double|t,r,e|15|2|None|  
|Zoned|S|1-30|Integer|t,r,e|5|None|None|  
|Zoned|S|1-30|Long|t,r,e|9|None|None|  
|Zoned|S|1-30|Single|t,r,e|15|2|None|  
|Unsigned|U|3-9|Byte|t,r,e|3|None|None|  
|Float|F|4|Decimal|t,r,e|None|None|None|  
|Float|F|8|Decimal|t,r,e|None|None|None|  
|Float|F|8|Double|t,r,e|8|None|None|  
|Float|F|4|Single|t,r,e|4|None|None|  
|Date|D|None|Date|None|None|None|None|  
|Time|None|None|None|None|None|None|None|  
|Time-stamp|None|None|None|None|None|None|None|  
  
|RPG Date format name|Format|Range|Bytes|  
|--------------------------|------------|-----------|-----------|  
|*MDY|mm/dd/yy|01/01/40 to 12/31/39|8|  
|*DMY|dd/mm/yy|01/01/40 to 31/12/39|8|  
|*YMD|yy/mm/dd|40/01/01 to 39/12/31|8|  
|*JUL|yy/ddd|40/001 to 39/365|6|  
|*ISO|yyyy-mm-dd|0001-01-01 to 9999-12-31|10|  
|*USA|mm/dd/yyyy|01/01/0001 to 12/31/0000|10|  
|*EUR|dd.mm.yyyy|01.01.0001 to 31.12.9999|10|  
|*JIS|yyyy-mm-dd|0001-01-01 to 9999-12-31|10|  
  
|RPG Time format name|Format|Range|Bytes|  
|--------------------------|------------|-----------|-----------|  
|*HMS|hh:mm:ss|00:00:00 to 24:00:00|8|  
|*ISO|hh.mm.ss|00:00:00 to 24:00:00|8|  
|*USA|hh:mm AM or hh:mm PM|00:00 AM to 12:00 AM|8|  
|*EUR|hh.mm.ss|00.00.00 to 24.00.00|8|  
|*JIS|hh:mm:ss|00:00:00 to 24:00:00|8|  
  
|RPG Timestamp Format|Bytes|  
|--------------------------|-----------|  
|yyyy-mm-dd-hh.mm.ss.mmmmmm|26|  
  
## See Also  
 [Supported TI Data Types](../core/supported-ti-data-types2.md)   
 [Converting Data Types from Automation to RPG](../core/converting-data-types-from-automation-to-rpg1.md)   
 [Data Type Conversion](../core/data-type-conversion1.md)