---
description: "Learn more about: Truncating Undefined Portions of Strings"
title: "Truncating Undefined Portions of Strings1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Truncating Undefined Portions of Strings
You can define the properties for a string such that the Transaction Integrator (TI) run-time environment truncates undefined characters when it converts UNICODE strings to mainframe data representations instead of generating an error message. To do so, click **Truncate** under **Error handling** on the string's **Host Definition** tab (property page) in TI Project.  
  
 When truncation is turned on, the TI run-time environment limits the number of characters to the string's previously specified dimension value when it converts a character string to an Extended Binary Coded Decimal Interchange Code (EBCDIC) or double-byte character set (DBCS) character string.  
  
 When it converts to intermixed strings, the TI run-time environment ensures that all shift-out (SO) characters have matching shift-in (SI) characters. It adds a terminating SI character when truncation occurs in the middle of a contiguous stream of DBCS characters. Also, the TI run-time environment ensures that it does not leave a partial DBCS character when it adds the SI character.  
  
 If blank padding and truncation are specified for a string, the TI run-time environment might need to add an EBCDIC space character after a terminating SI character is added.  
  
## See Also  
 [Converting Data Types from Automation to z/OS COBOL\]](../core/converting-data-types-from-automation-to-os-390-cobol]2.md)   
 [Converting Data Types from z/OS COBOL to Automation](../core/converting-data-types-from-os-390-cobol-to-automation2.md)
