---
title: "How to Pass a Custom TRM2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bb2602e-1387-48b3-b7e3-7d8dc3e3904e
caps.latest.revision: 3
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
 [ClearAllContext](../core/clearallcontext.md)   
 [CountContext](../core/countcontext.md)   
 [DeleteContext](../core/deletecontext.md)   
 [QueryContextInfo](../core/querycontextinfo.md)   
 [ReadContext](../core/readcontext.md)   
 [WriteContext](../core/writecontext.md)   
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext.md)