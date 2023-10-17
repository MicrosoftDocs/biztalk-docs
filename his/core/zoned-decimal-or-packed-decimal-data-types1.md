---
description: "Learn more about: Zoned Decimal or Packed Decimal Data Types"
title: "Zoned Decimal or Packed Decimal Data Types1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Zoned Decimal or Packed Decimal Data Types
When it imports a host data declaration, Transaction Integrator (TI) converts Zoned Decimal (COBOL numeric PIC with DISPLAY or no USAGE, or RPG S data type) or Packed Decimal data types to Decimal or Currency Automation data types, respectively. Depending on the development application you are using, there might not be an equivalent for Decimal or Currency data types. If this is the case, use one of the following techniques to ensure that the data type works correctly with TI:  
  
-   Use language-supplied functions to manipulate the Automation types for Decimal or Currency.  
  
-   Within TI Project, if the data type has a fractional component, modify the method's parameter from the Decimal or Currency data type to the Floating Point Binary data type (double or single precision as appropriate). You can substitute a 16-bit or 32-bit binary Integer data type if the data declaration has no fractional component and the number of data declaration digits fits within the expected range.  
  
> [!NOTE]
>  When you use the Floating Point Binary data type, the likelihood of a data conversion precision problem increases if fractions are involved. TI offers three options to handle data precision errors: Round (default), Truncate, or Error. The double-precision Floating Point Binary data type can handle host data declarations of up to fifteen digits.  
  
## See Also  
 [COBOL FILLER](../core/cobol-filler1.md)   
 [How to Use REDEFINES in COBOL](../core/how-to-use-redefines-in-cobol1.md)
