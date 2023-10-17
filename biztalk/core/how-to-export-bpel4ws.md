---
description: "Learn more about: How to Export BPEL4WS"
title: "How to Export BPEL4WS | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BPEL4WS, exporting"
  - "BPEL4WS, restrictions"
  - "orchestrations, BPEL4WS"
ms.assetid: 4648dfcf-cf48-4471-b088-07252c080fb8
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export BPEL4WS
You can export an existing BizTalk orchestration to BPEL4WS.  
  
> [!IMPORTANT]
>  This release of BizTalk Server supports BPEL4WS 1.1. You cannot import or export BPEL4WS 1.0.  
  
 If you are exporting, BPEL4WS compliance for compilation requires that orchestrations contain only features that are common between XLANG/s and BPEL4WS, or features that can be translated into BPEL4WS without affecting behavior.  
  
## Export restrictions on orchestrations for BPEL4WS compliance  
  
-   You cannot use the Call Orchestration shape or the Start Orchestration shape.  
  
-   You cannot use the Transform shape.  
  
-   You cannot invoke methods on custom .NET components.  
  
-   You cannot apply a timeout to a long-running transaction.  
  
-   Your orchestration cannot take parameters.  
  
-   Callable compensation handlers cannot have parameters.  
  
-   Variable types must be supportable in XPATH.  
  
-   You cannot use the Suspend shape.  
  
-   Literal values must be one of the following types:  
  
     boolean, char, byte, sbyte, int32, uint32, int64, uint64, single, double, string  
  
-   Arithmetic operators are allowed only on operands of following numeric types:  
  
     byte, sbyte, int32, uint32, int64, uint64, single, double  
  
-   Relational operators cannot be applied to type char.  
  
-   You cannot make a reference to a servicelink property in an expression.  
  
-   You cannot perform any actions between a **Send** shape and a **Receive** shape that use the same outbound request-response port.  
  
-   You cannot indirectly reference a web service, as through a reference to another project that contains a reference. You must explicitly reference the web service in your project.  
  
-   You cannot specify a constant DateTime or TimeSpan in a delay. Instead, use one of the conversion classes in the System.Xml namespace:  
  
     For a constant DateTime: System.Xml.XmlConvert.ToDateTime, e.g System.Xml.XmlConvert.ToDateTime("2004-04-15")  
  
     For a constant TimeSpan: System.Xml.XmlConvert.ToTimeSpan, e.g System.Xml.XmlConvert.ToTimeSpan("2004-04-15")  
  
> [!NOTE]
>  Character literals are exported as unsigned integers. For example, 'a' is exported as 97, 'b' is exported as 98, and so forth.  
  
> [!CAUTION]
>  Identifier names must conform to the W3C Extensible Markup Language (XML) 1.0 specification.  
  
#### To export an orchestration to BPEL4WS  
  
1.  Add a new item of type BizTalk Orchestration to your project.  
  
2.  Click the design surface to bring up the Orchestration Properties window.  
  
3.  Set **Module Exportable** to True.  
  
4.  Type in the namespace you want for **Module XML Target Namespace**.  
  
5.  Set **Orchestration Exportable** to True.  
  
6.  Type in the namespace you want for **Orchestration XML Target Namespace**.  
  
7.  In Solution Explorer, right-click the .ODX file for your orchestration.  
  
8.  Select **Export to BPEL**.  
  
     Your orchestration will be exported to BPEL4WS. See the Output Window and Task List to confirm success or diagnose problems. Once your export succeeds, a .WSDL file and a .BPEL file will be created in your project directory.  
  
> [!NOTE]
>  If your orchestration contains an assignment to a role link (service link) or a literal assignment to a dynamic port, BizTalk generates a dummy BPEL4WS endpoint reference and raises a warning.  
  
## See Also  
 [How to Import BPEL4WS](../core/how-to-import-bpel4ws.md)   
 [XLANG-s to BPEL4WS Type Conversions](../core/xlang-s-to-bpel4ws-type-conversions.md)
