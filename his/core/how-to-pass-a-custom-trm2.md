---
description: "Learn more about: How to Pass a Custom TRM"
title: "How to Pass a Custom TRM2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bb2602e-1387-48b3-b7e3-7d8dc3e3904e
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Pass a Custom TRM
The following code example demonstrates passing a custom transaction request message (TRM).  
  
```  
' You must set the following references in your project:  
  
' Microsoft.HostIntegration.TI.ClientContext.dll  
' Microsoft.HostIntegration.TI.Globals.dll  
  
Imports Microsoft.HostIntegration.TI  
  
Dim ELMINsend As TIComponent.ELMINStructure  
Dim ELMOUTreturn As TIComponent.ELMOUTStructure  
  
Dim TIContext As New  ClientContext  
  
ELMINsend.progname = "CUSELM01"  
ELMINsend.member1 = "CE01,"  
ELMINsend.member2 = "AAAAAAAAAA"  
ELMINsend.member3 = CShort(2)  
ELMINsend.member4 = "  "  
  
ELMOUTreturn.member1 = CShort(0)  
ELMOUTreturn.member2 = ""  
  
TIContext.TransportHeaders.HeaderToBeforeDataSent = ELMINsend  
TIContext.TransportHeaders.HeaderFromAfterDataSent = ELMOUTreturn  
  
RunObj.MethodCall(parameter1, TIContext)  
```  
  
## See Also  
 [ClearAllContext](../core/clearallcontext1.md)   
 [CountContext](../core/countcontext1.md)   
 [DeleteContext](../core/deletecontext2.md)   
 [QueryContextInfo](../core/querycontextinfo1.md)   
 [ReadContext](../core/readcontext1.md)   
 [WriteContext](../core/writecontext1.md)   
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext2.md)
