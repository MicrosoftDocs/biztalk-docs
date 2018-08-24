---
title: EDI Instance Properties Dialog Box UI Help
TOCTitle: EDI Instance Properties Dialog Box UI Help
ms:assetid: a0d3c0eb-72c8-4142-ad24-6c75371fac76
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb743625(v=BTS.80)
ms:contentKeyID: 51530137
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.edir2.edi.instance.properties
---

# EDI Instance Properties Dialog Box UI Help

 

This topic describes the fields in the EDI Instance Properties dialog box. These fields specify separators and identifiers used in the EDI instance generated for a schema. This page is displayed by right-clicking a schema in a BizTalk project in Visual Studio, and then clicking **Generate Instance**.

## EDI Instance Properties Fields

Data element separator (4th char in ISA)  
Select **Char** or **Hex** from the drop-down list, and then select the data element separator to be used in the EDI instance generated from the schema.

The default value is **\*** in **Char**.

Component element separator (ISA16)  
Select **Char** or **Hex** from the drop-down list, and then select the component element separator to be used in the EDI instance generated from the schema.

The default value is **:** in **Char**.

Standard identifier (ISA11 Usage)  
To use a standard identifier for ISA11 in the EDI instance generated from the schema, click the **Standard Identifier** radio box, and then select the standard identifier.

The default is **U - U.S. EDI Community of ASC X12, TDCC and UCS**.

Repetition separator (ISA11 Usage)  
To use a Repetition separator for ISA11 in the EDI instance generated from the schema, click the **Repetition separator** radio box, and then select the Repetition separator.

The default value is **^**. This element is limited to the values in the ASCII character set.

Segment separator (106th char of ISA)  
Select **Char** or **Hex** from the drop-down list, and then select the segment separator to be used in the EDI instance generated from the schema.

The default value is **~** in **Char**.

Segment separator suffix  
Select the suffix to be used with the segment separator in the EDI instance generated from the schema. Can be either **None**, **CR** (carriage return), **LF** (line feed), or **CR LF** (carriage return/line feed).

Use trailing delimiters  
Select **Yes** to use trailing delimiters in the EDI instance generated from the schema.

The default value is **No**.

Syntax identifier  
Select the syntax to be used in the EDI instance generated from the schema. Can be **Basic**, **Extended**, or **UTF8/Unicode**.

The default value is **UTF8/Unicode**.

Error/Information  
An error information about the instance is displayed in the Error/Information pane.

Help  
Click to display this topic.

OK  
Click to accept the displayed values.

Cancel  
Click to reject the displayed values, and use the previous values.

