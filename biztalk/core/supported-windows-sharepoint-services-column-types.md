---
title: "Supported Windows SharePoint Services Column Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [Windows SharePoint Services adapters], supported column types"
  - "Windows SharePoint Services adapters, supported column types"
ms.assetid: 14992f52-9d18-4321-9152-83c8a37751bc
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Supported Windows SharePoint Services Column Types
This topic describes the Windows SharePoint Services column types that are supported by the Windows SharePoint Services adapter. The values of these column types can be set in the message.  

> [!NOTE]
>  Calculated columns are not updated by the adapter.  

## Supported types  
 The following table describes the supported column types:  


|           UI Type           | SharePoint Object Model Type |                    Sample                    |                                                                                                                                                                                                                                                                            Comments                                                                                                                                                                                                                                                                            |
|-----------------------------|------------------------------|----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     Single Line of Text     |       SPFieldType.Text       |                 single line                  |                                                                                                                                                                                                                                                                              None                                                                                                                                                                                                                                                                              |
|   Multiple lines of text    |       SPFieldType.Note       | line 1<br /><br /> line 2<br /><br /> line 3 |                                                                                                                                                                                                                                                                              None                                                                                                                                                                                                                                                                              |
|      Choice Drop-Down       |      SPFieldType.Choice      |                   ChoiceA                    |                                                                                                                                                                                                                                                 ChoiceA from the available choices (ChoiceA, ChoiceB, ChoiceC)                                                                                                                                                                                                                                                 |
|    Choice Radio-Buttons     |      SPFieldType.Choice      |             #ChoiceB;#ChoiceC;#              |                                                                                                                                                                                                                 ChoiceB and ChoiceC are enabled, ChoiceA is disabled (available choices are ChoiceA, ChoiceB, ChoiceC). Use ;# as a separator.                                                                                                                                                                                                                 |
|           Number            |      SPFieldType.Number      |                   123.456                    |                                                                                                                                                                                                                                                                              None                                                                                                                                                                                                                                                                              |
| Currency USD (or any other) |     SPFieldType.Currency     |                    100.00                    |                                                                                                                                                                                                                                                                              None                                                                                                                                                                                                                                                                              |
|           Lookup            |      SPFieldType.Lookup      |                      1                       |                                                                                                                                                                                                                                                 The number is the item identifier inside the referenced list.                                                                                                                                                                                                                                                  |
|            YesNo            |     SPFieldType.Boolean      |                      1                       |                                                                                                                                                                                                                                                                     1=Yes<br /><br /> 0=No                                                                                                                                                                                                                                                                     |
|    Hyperlink or Picture     |       SPFieldType.URL        | http://www.microsoft.com, Microsoft Web Site |                                                                                                                                                                                                                  URL separated with "," from the display text. The "Microsoft Web Site" text will be a hyperlink to http://www.microsoft.com                                                                                                                                                                                                                   |
|        Date and Time        |     SPFieldType.DateTime     |             2005-02-11T10:05:04              | The DateTime as defined by the XML standard for the xs:dateTime. The pattern for dateTime is CCYY-MM-DDThh:mm:ss where CC represents the century, YY the year, MM the month, and DD the day, preceded by an optional leading negative (-) character to indicate a negative number. If the negative character is omitted, positive (+) is assumed. The T is the date/time separator and hh, mm, and ss represent hour, minute, and second, respectively. This representation may be immediately followed by a "Z" to indicate UTC or to indicate the time zone. |

## See Also  
 [How to Configure a Windows SharePoint Services Receive Location](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [How to Configure a Windows SharePoint Services Send Handler](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [How to Configure a Windows SharePoint Services Send Port](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [How to Create a Send Port](../core/how-to-create-a-send-port2.md)   
 [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Windows SharePoint Services Adapter Expressions](../core/windows-sharepoint-services-adapter-expressions.md)