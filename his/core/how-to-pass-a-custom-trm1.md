---
title: "How to Pass a Custom TRM1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44c55493-646f-4894-bc03-46c0a2306176
caps.latest.revision: 4
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
 [ClearAllContext](../core/clearallcontext2.md)   
 [CountContext](../core/countcontext2.md)   
 [DeleteContext](../core/deletecontext1.md)   
 [QueryContextInfo](../core/querycontextinfo2.md)   
 [ReadContext](../core/readcontext2.md)   
 [WriteContext](../core/writecontext2.md)   
 [Custom TRMs and ELMs with COMTIContext](../core/custom-trms-and-elms-with-comticontext1.md)