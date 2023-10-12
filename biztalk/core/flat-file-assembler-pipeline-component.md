---
description: "Learn more about: Flat File Assembler Pipeline Component"
title: "Flat File Assembler Pipeline Component"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Flat File Assembler Pipeline Component
A Flat File Assembler combines individual documents into a batch and optionally adds a header or trailer (or both) to it. For more information about flat files, see [Flat File Messages with Delimited Records](../core/flat-file-messages-with-delimited-records.md). Also see [Flat File Messages with Positional Records](../core/flat-file-messages-with-positional-records.md).  
  
 The Flat File Assembler pipeline component does not validate the incoming XML message. To ensure XML validation, include the XML Validator component in the Pre-Assemble stage of the send pipeline.  
  
 The Flat File Assembler pipeline component only supports conversions supported by the Microsoft .NET Framework. Any additional conversion can be done by writing to a custom text writer.  
  
 For information about configuring the Flat File Assembler pipeline component, see [How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md).  
  
> [!NOTE]
>  In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you cannot assemble messages into one interchange.  
  
## In This Section  
  
-   [Character Encoding in the Flat File Assembler Pipeline Component](../core/character-encoding-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [Document Structure Enforcement in the Flat File Assembler Pipeline Component](../core/document-structure-enforcement-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [Retaining Delimiters in the Flat File Assembler Pipeline Component](../core/retaining-delimiters-in-the-flat-file-assembler-pipeline-component.md)
