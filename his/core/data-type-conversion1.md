---
title: "Data Type Conversion1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 46739014-e868-407c-ae6d-c5b7fc656c97
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Type Conversion
The Transaction Integrator (TI) run-time environment automatically converts data types between host-based COBOL or Report Program Generator (RPG) data types and the COM-based Automation data types that a Windows-based programming language like Visual Basic uses. The automatic conversion is based on information that you define in TI Project when you design and create a TI component (type library). This information is stored with the TI component and used by the TI runtime to convert the parameters of a method from the representation understandable by a COM-based or .NET-based programming language into the representation understandable by a host transaction program (TP).  
  
 Use TI Project to associate each Automation data type with each COBOL or RPG data type used in the host TP. TI provides default mappings between standard Automation data types and COBOL or RPG data types. You can either accept the default mappings or override the default with other mappings supported by TI. TI Project stores the conversion map in the TI component type library (.tlb) file. This conversion map is used to:  
  
- Handle data moving between the TP and the TI component.  
  
- Convert a TI component into a TP (export the host definition).  
  
- Convert a TP into a TI component (import the host definition).  
  
  If a parameter used in a method call is not strictly typed, the TI run-time environment attempts to coerce the data type it receives into the data type it expects. If that coercion is successful, the call proceeds. If it is unsuccessful, an error is returned.  
  
  At run time, when a client application uses the TI Automation interface to call a method of the TI Automation server, the TI run-time environment uses the conversion map to handle the actual data conversion of the in and in/out parameters being sent to the mainframe TP. After TI converts the Microsoft® Windows® data, TI reformats the method call as a host system APPC/LU 6.2 or TCP/IP message. Then TI uses Microsoft Host Integration Server SNA or TCP/IP connectivity to forward the message to the mainframe. When the mainframe TP returns the in/out and out parameters, TI reformats the message for the return to Windows, converts the host data into Windows data, and returns the return value and parameters to the client application.  
  
  The choice of language or code page you made in TI Manager when you defined the remote environment (RE) determines which code page is used to convert from UNICODE (on the Automation side) to Extended Binary Coded Decimal Interchange Code (EBCDIC) (on the mainframe side). When you create an RE in TI Manager, you can either select a language to accept the default code page for that language, or select a specific code page.  
  
  If you need to convert to different target code pages (if you have, for example, target mainframes in different countries or regions), you need to set up an RE for each target because TI does not support conversions requiring the use of locale.  
  
  You can use TI Project to import COBOL or RPG, or to manually enter method descriptions to create Automation methods. When you import COBOL or RPG, each supported COBOL data type has a default Automation type. When you manually create a method, each Automation data type has a default host data type associated with it.  
  
  If you do not want to use a default Automation data type, you can use TI Project to change the Automation data type manually. If the new Automation type is compatible with the existing host data type, the existing COBOL or RPG data type is left unchanged. If it is not compatible, the host data type is changed, thus affecting your mainframe program.  
  
## In This Section  
  
-   [Converting Data Types from Automation to OS/390 COBOL](../core/converting-data-types-from-automation-to-os-390-cobol]2.md)  
  
-   [Converting Data Types from OS/390 COBOL to Automation](../core/converting-data-types-from-os-390-cobol-to-automation2.md)  
  
-   [Converting Data Types from Automation to RPG](../core/converting-data-types-from-automation-to-rpg1.md)  
  
-   [Converting Data Types from RPG to Automation](../core/converting-data-types-from-rpg-to-automation1.md)  
  
-   [Zoned Decimal or Packed Decimal Data Types](../core/zoned-decimal-or-packed-decimal-data-types1.md)  
  
-   [Converting Data Types from RPG to OS/400 COBOL](../core/converting-data-types-from-rpg-to-os-400-cobol2.md)