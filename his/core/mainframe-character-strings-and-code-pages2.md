---
title: "Mainframe Character Strings and Code Pages2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 068ddf61-61bd-4313-b1c9-ccea073fb876
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Mainframe Character Strings and Code Pages
When Transaction Integrator (TI) sends data to a mainframe-based transaction program (TP), the TI run-time environment transforms Unicode strings received as parameters, fields, or columns into mainframe character strings. Likewise, when it receives data from a mainframe TP, the TI run-time environment converts the mainframe character strings into Unicode strings to be returned as output values to the calling client application.  
  
 TI categorizes these strings of characters sent to and received from the mainframe as follows:  
  
- Extended Binary Coded Decimal Interchange Code (EBCDIC) strings.  
  
- IBM double-byte character set (DBCS) strings.  
  
- Intermixed strings containing both EBCDIC and IBM DBCS strings with the necessary shift-out (SO) and shift-in (SI) characters.  
  
  The TI run-time environment determines the type of mainframe character string based on the following information:  
  
- How the parameter, field, or column is defined in the TI component that was built by using TI Project.  
  
- The code page defined for the specific remote environment (RE) that was associated with the active TI Automation server when it was deployed. When you create an RE in TI Manager, you specify a code page for that RE.  
  
## In This Section  
 [How to Assign a Different Code Page to a Remote Environment](../core/how-to-assign-a-different-code-page-to-a-remote-environment2.md)  
  
 [IBM DBCS Code Pages](../core/ibm-dbcs-code-pages1.md)  
  
 [Mainframe Character Formats](../core/mainframe-character-formats2.md)  
  
 [How to Pad Mainframe Character Strings with Spaces](../core/how-to-pad-mainframe-character-strings-with-spaces2.md)  
  
 [Truncating Undefined Portions of Strings](../core/truncating-undefined-portions-of-strings1.md)  
  
 [Adding Leading SO and Trailing SI Characters](../core/adding-leading-so-and-trailing-si-characters1.md)