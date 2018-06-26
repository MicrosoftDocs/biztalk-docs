---
title: "Using the MATH_NUMERIC Type1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters [JD Edwards EnterpriseOne adapters], currency"
  - "JD Edwards EnterpriseOne adapters, exponents"
  - "adapters [JD Edwards EnterpriseOne adapters], exponents"
  - "MATH_NUMERIC type"
  - "currency, values [JD Edwards EnterpriseOne adapters]"
  - "JD Edwards EnterpriseOne adapters, currency"
  - "exponents, values [JD Edwards EnterpriseOne adapters]"
ms.assetid: 2a302216-f0a6-4afb-8f7d-bb1475ea1c57
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the MATH_NUMERIC Type
This topic describes the MATH_NUMERIC type and details how exponents are handled, the maximum number of digits, and the maximum number of decimal digits. It also includes a discussion on:  
  
- Exponents  
  
- Invalid Values  
  
- Precision for Operations  
  
- Currency  
  
  The MATH_NUMERIC type is a numeric string type. To use it, enter parameter values of the following format:  
  
```  
<OptionalSign><IntegerAndFractionalPart><OptionalExponentPart>  
  
```  
  
 Where  
  
 `<OptionalSign>` can be `+` or `-`. `+` is the default.  
  
 `<IntegerAndFractionalPart>` is a maximum of 32 significant digits, not counting the decimal symbol. The decimal symbol is locale-specific to the JD Edwards EnterpriseOne installation—typically a period (.) or a comma (,). The digits may be all integer, all fraction, or part integer and part fraction, but they cannot exceed 32.  
  
 `<OptionalExponentPart>` is equivalent to:  
  
```  
'e' <OptionalSign><ExponentDigits>  
```  
  
 Where  
  
 `<OptionalSign>` can be `+` or `-`. `+` is the default.  
  
 `<ExponentDigits>` are at most two digits. You are permitted values between 63 and -63 excluding zero.  
  
## Valid Values  
 Examples of **valid** MATH_NUMERIC values:  
  
-   123.045  
  
-   4089 (note there is no comma for thousands)  
  
-   -9084  
  
-   -230.75  
  
-   0.010503  
  
-   1.023e-10, which is equivalent to 0.0000000001023  
  
-   0.097e5 or 0.097e+5, which is equivalent to 9700  
  
-   1.0e-32, which is equivalent to 0.00000000000000000000000000000001 (This is valid because in this case, the integral '0' is ignored, 32 significant fractional digits.)  
  
## Invalid Values  
 Invalid values depend on the kind of value. A decimal fraction that is too small is interpreted as zero (all significant digits are lost). An integer that has too many significant digits causes unexpected results. JD Edwards EnterpriseOne does not always raise an error condition in this case. An exponent that is too large or too small also returns as an invalid value.  
  
 Examples of **invalid** MATH_NUMERIC values:  
  
- 1034.00000000000000000000000000001023 - too many significant digits  
  
- 1.023e-64 - exponent too small  
  
- 0.00317e64 - exponent too large  
  
  Any non-numeric characters other than those appropriate for signs and decimal symbols result in an invalid value.  
  
## Exponents  
 Exponents are provided by the JD Edwards EnterpriseOne MATH_NUMERIC as a convenience for entering values. However, most values return without exponents (with all 32 significant digits visible).  
  
## Precision for Operations  
 If an operation results in loss of precision, rounding occurs. For example:  
  
 1.9e-31 / 10.0 = 0.00000000000000000000000000000002.  
  
 1.9e-31 / 100.0 = 0.00000000000000000000000000000000  
  
 In other cases, unpredictable results occur, as when a very large positive value is multiplied by another. 1.01e32 * 2.053e32 does not yield reliable results and does not raise an error. For most business scenarios, these ranges are not exceeded.  
  
## Currency  
 When a JD Edwards EnterpriseOne business function expects a currency value, the business function always has a separate parameter for a four-character currency code. It is not necessary to pass in this code unless you are using a currency other than the default configured for the JD Edwards EnterpriseOne system.  
  
## See Also  
 [Appendix B: Data Types](../core/appendix-b-data-types.md)