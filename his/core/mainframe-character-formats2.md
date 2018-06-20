---
title: "Mainframe Character Formats2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d956658-7076-4e53-b82f-cb8811692bbf
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Mainframe Character Formats
In Transaction Integrator (TI) Project, you can specify the mainframe character format that the TI run-time environment will create when sending data to the mainframe. There are two mainframe character formats supported by TI:  
  
- PIC X(n) COBOL, or RPG A  
  
- PIC G(n) COBOL, or RPG G  
  
  When you create string parameters, fields, or columns in TI Project, the PIC X(*n*) or RPG A data type format is selected automatically.  
  
  If necessary, you can use the **Properties** command to change the mainframe character format.  
  
  If you select the PIC X or RPG A format for a string, the TI run-time environment converts this string to either an Extended Binary Coded Decimal Interchange Code (EBCDIC) character string or an intermixed character string. Specifically, if the TI component you define in TI Project is assigned to a remote environment (RE) with an EBCDIC code page, the TI run-time environment converts a string that has a PIC X or RPG A format into an EBCDIC string. If the TI component's RE identifies a double-byte character set (DBCS) code page, the TI run-time environment converts a string that has a PIC X format as an intermixed string (not supported for RPG).  
  
  If you select the PIC G or RPG G format for a string, the TI run-time environment always converts the string into a DBCS string. Therefore, any TI component that uses a string with a PIC G or RPG G format must be assigned to an RE that has a DBCS code page.  
  
  If a TI component using a string with a PIC G or RPG G format is assigned to an RE that has an EBCDIC code page, the TI run-time environment reports a conversion error when it attempts to convert the string to or from the PIC G or RPG G format. The TI run-time environment places an error message describing this conversion problem in the Windows Event Log, and it returns an error to the invoking client application.  
  
  The following table summarizes how the selection of string format and code page controls the type of character conversion performed by the TI run-time environment.  
  
|String format|EBCDIC code page|DBCS code page|  
|-------------------|----------------------|--------------------|  
|PIC X or RPG A|EBCDIC string|Intermixed string|  
|PIC G or RPG G|TI run-time environment reports conversion errors.|DBCS string|  
  
## String Dimension Values  
 The meaning of a string's dimension (the *n* part of the PIC X(n) or RPG A(n) and the *n* part of the PIC G(n) or RPG G(n) formats) is based on the character format in use. You specify a string's dimension on the **COBOL Definition** property page in Transaction Integrator (TI) Project.  
  
- The dimension value for a string with a PIC G or RPG G format gives the number of double-byte characters that are used in the mainframe representation of the string. No SO and SI character pair is added when a string with a PIC G or RPG G format is converted.  
  
- The dimension value for a string with a PIC X or RPG A format gives the number of bytes that are used in its mainframe representation. The number of characters that can be placed into or taken from a PIC X or RPG A formatted string varies depending on the number of :  
  
  -   Double-byte character set (DBCS) characters, each of which requires two bytes of storage.  
  
  -   SO and SI character pairs needed. Each two-byte pair must encapsulate each contiguous stream of DBCS characters.  
  
  Developers using TI must take into account this variability in the size of an intermixed string when they specify dimension values in TI Project.  
  
  The number of bytes for a string converted using an EBCDIC code page with a PIC X or RPG A format is identical to the number of characters because there are no DBCS characters in the string.  
  
  However, for a string converted using a DBCS code page with a PIC X or RPG A format, the actual number of characters that can be placed in a given number of bytes varies. For example, if the conversion to or from UNICODE does not require the use of DBCS characters (that is, no SO and SI character is used in the mainframe string), each character occupies a single byte. However, if DBCS characters do appear within the mainframe string, the SO and SI character pairs are needed.  
  
## How the Import Wizard Defines Strings  
 When you use Transaction Integrator (TI) Project's Import wizard to import a host definition to create new methods and recordsets, the wizard selects the mainframe character format based on the imported host definition. The following table shows how the wizard maps different COBOL declarations to a string.  
  
|COBOL type|Type of string created|  
|----------------|----------------------------|  
|PIC X(*n*) or RPG A|String of size *n* bytes|  
|PIC G(*n*) or RPG G|String of size *n* characters|  
  
## See Also  
 [Mainframe Character Strings and Code Pages](../core/mainframe-character-strings-and-code-pages2.md)