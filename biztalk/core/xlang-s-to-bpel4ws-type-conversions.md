---
title: "XLANG-s to BPEL4WS Type Conversions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XLANG/s"
  - "XLANG/s, warning"
  - "XLANG/s, BPEL4WS"
  - "XLANG/s, converting"
ms.assetid: a35d4dba-9344-43c8-86e6-a373a4452579
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XLANG-s to BPEL4WS Type Conversions
The following tables detail the conversions between various XLANG/s constructs and BPEL4WS constructs.  
  
> [!CAUTION]
>  XPath 1.1 does not support numbers in exponential or double formats. Literal values in these formats in XLANG/s orchestrations are exported to BPEL4WS using the %f format, and a loss of precision might result.  
  
## Literals (if the literal is part of an expression)  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|String, character|XPath string|  
|Integer, real|XPath number|  
|Boolean "true", "false"|XPath true(), false() functions|  
  
## Literals (standalone assignment)  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|Literal constant|XSD equivalent|  
  
## Variables  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|Variable reference|bpws:getContainerData(%varName%,  part, %locationPath%)|  
|Message reference (.NET type)|bpws:getContainerData(%msgName%, part, %locationPath%)|  
|Message-part reference|bpws:getContainerData(%msgName%, %locationPath%)|  
|Distinguished-field reference|bpws:getContainerData(%msgName%, %partName%, %locationPath%)|  
|Message data-property reference|bpws:getContainerProperty(%msgName%, %propertyQName%)|  
  
## Operators  
  
|XLANG/s|BPEL4WS|  
|--------------|-------------|  
|Unary +|Ignored|  
|Unary -|XPath unary -|  
|Unary !|XPath not() function|  
|Binary &&, &#124;&#124;|XPath 'and', 'or' operators|  
|Binary ==, !=, <=, \<, >=, >|XPath '=', '! =', '<=', '\<', '>=', '>' operators|  
|Binary +, -, *, % with both integral operands|XPath '+', '-', '*', 'mod' operators|  
  
## XLANG/s constructs that are disallowed in BPEL4WS  
  
-   Message context-property reference  
  
-   Service-property reference  
  
-   Port-property reference  
  
-   Service link-property reference  
  
-   Unary – with non-integral type  
  
-   Unary ~  
  
-   Cast operator  
  
-   Binary / with integral operands  
  
-   Binary +, -, *, %, / with non-integral operands  
  
-   Binary <=, \<, >=, > with non-string operands  
  
-   Bitwise operators &, ^, &#124;  
  
-   Shift operators <\<, >>  
  
-   Checked expression  
  
-   Intrinsic expression  
  
-   Pre- and post- increment and decrement ++, --  
  
-   Object invocation (with our without out and/or ref params)  
  
-   'new' operator