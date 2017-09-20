---
title: "International Considerations for Designing BizTalk Applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9daaaaf7-6149-4e62-9e9b-b6356fc820d2
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# International Considerations for Designing BizTalk Applications
It is strongly recommended that you review the following known issues when you develop your international [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications.  
  
 **Character Restrictions for Machine Names**  
  
 Installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on machines with names that contain letters outside of the following set is not supported: letters (A-Z, a-z), digits (0-9), hyphens (-), and underscores ( _ ). Only machine names that contain the letters in this set are supported.  
  
 **Characters do not appear correctly or do not appear at all due to incorrect font and font fallback settings**  
  
 You may experience issues displaying characters (such as Czech characters) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tools hosted in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To address these issues, you may need to modify the font settings available in the Visual Studio Options tab and select another font that you know supports the characters. You can select Tahoma or Microsoft Sans Serif as the default font for which font fallback capabilities are provided.  
  
 **Surrogate pair characters displayed as squares in BizTalk Server Administration console and other BizTalk Server tools**  
  
 You may not be able to display surrogate pair characters in BizTalk Server Administration Console and other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tools. Surrogate pairs are a coded character representation for a single abstract character that consists of a sequence of two code units. Make sure you have the appropriate font installed on your system (it is included in the Chinese versions of Office XP and 2003). It may also be necessary to change the font options in the tools that have such capability (such as [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]).  
  
 In other tools without a font setting option, surrogate pair characters will be displayed as squares, such as the Administration console. If you see squares, the characters are not corrupted; they just cannot be displayed properly because of a lack of font support.  
  
 **Web Services character limitations**  
  
 If you plan on publishing an orchestration as a Web Service, you may encounter issues with characters used in the orchestration names and port names as those names are used in the Web Services file names (.asmx files) and the virtual directory in the Web Services Publishing Wizard. Only Microsoft Internet Information Services (IIS) 7.0 (included in Microsoft Windows Server 2008 and Windows Vista) fully supports Unicode characters. Therefore, if you use an earlier version of IIS or Windows, the names of the orchestrations, ports, Web services and virtual directories names must include only ANSI characters supported by the language version of Windows (for example, Japanese characters are not allowed on an English version of Windows).  
  
 Note also that project names for Web Services in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] are restricted to ASCII characters.  
  
 **Working with different document encodings**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports many different encodings for XML and flat file documents, for example UTF-16, UTF-8, Simplified Chinese GBK, Simplified Chinese GB18030, and so on.  
  
 For inbound documents, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can recognize the encoding declaration in XML documents, such as "\<?xml version="1.0" encoding="GB2312" ?>". The flat file schema has a **Code Page** property to indicate the encoding of the inbound flat file documents.  
  
 For outbound documents, XML and flat file assemblers use the **Target charset** property. If this property is specified, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] converts the outbound documents to the specified character set regardless of the original one. If no **Target charset** property is set, XML uses the UTF-8 protocol and flat files use the code page specified in the flat file schema.  
  
 **Code Conversion from an unsupported code page to a Windows code page**  
  
 To implement code conversions from unsupported code pages into a Windows code page, you must create a custom pipeline component.  
  
 **Byte-order mark impact on document encoding**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines character encoding and produces documents with a particular character encoding differently for flat file and XML messages.  
  
 **Schema Editor may contain properties in more than one language**  
  
 XML Schema Definition language (XSD) property names shown in the Schema Editor Properties window and in the XML source code are not localized, and appear in English in all localized versions. Other properties are shown in the local language. For example, in the simplified Chinese version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the schema properties are in English, but additional properties are displayed in Chinese.  
  
 **Locale-dependent data in flat files**  
  
 Many locales represent data such as date, time, number, and currency using different formats than those formats defined in the XML standard. For instance, several locales use a decimal separator other than a period (.), so the number five and three quarters may be represented as 5,75.  
  
 In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], all fields from flat files except date and time are treated as strings, so that parsing can succeed. However, when using XML validation, the resulting XML message fails during validation against the schema.  
  
 For date and time fields, the parser attempts to parse the field value to the DateTime instance using a custom date or time format if it is defined, and writes it in XML format, or uses the original value as a string if date or time format is not defined. Again, if XML validation is used, the resulting date or time may fail validation if a custom date or time format is not used, and the field value used in flat file message was not in the correct XML date or time format.  
  
 Note that you can also create custom pipeline components or maps to update field values to produce valid XML.  
  
 **BAM definition language support**  
  
 Before you can deploy a BAM definition XML file, you must ensure that the language used to create this file matches the locale settings of the computer on which it is being deployed. If the file and the computer settings dont match, you must first reboot the computer used to run the BM.exe.  
  
> [!NOTE]
>  The BAM definition XML file cannot contain text in multiple languages unless the languages all use the same codepage or only two languages are included and one of them is English.  
  
## See Also  
 [Implementing Character Encoding in a Pipeline Component](../core/implementing-character-encoding-in-a-pipeline-component.md)   
 [Handling Encoding in a Disassembler Pipeline Component](../core/handling-encoding-in-a-disassembler-pipeline-component.md)   
 [Character Encoding in the Flat File Disassembler Pipeline Component](../core/character-encoding-in-the-flat-file-disassembler-pipeline-component.md)   
 [Character Encoding in the Flat File Assembler Pipeline Component](../core/character-encoding-in-the-flat-file-assembler-pipeline-component.md)   
 [Character Encoding in the XML Assembler Pipeline Component](../core/character-encoding-in-the-xml-assembler-pipeline-component.md)   
 [Character Encoding in XML Disassembler Pipeline Component](../core/character-encoding-in-xml-disassembler-pipeline-component.md)