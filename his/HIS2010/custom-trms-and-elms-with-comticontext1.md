---
title: "Custom TRMs and ELMs with COMTIContext1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df7db4d6-e84e-491a-b55f-0a46888ff1fd
caps.latest.revision: 3
---
# Custom TRMs and ELMs with COMTIContext
Transaction Integrator (TI) developers can pass custom formatted transaction request messages (TRMs) or enhanced listener messages (ELMs) from a client program to the CICS system and receive custom formatted TRMs or ELMs.  
  
 Custom TRMs or ELMs are passed through context data. The context data is contained in the optional *COMTIContext* parameter defined in the client application code and must be the final parameter in the method call. A TRM destined for the host must be defined as a user-defined type (UDT) for the COM model, or a structure for the .NET Framework model. The name of the UDT must begin with the characters TRMIN. A TRM reply from the host must also be defined as a UDT. The name of the UDT must begin with the characters TRMOUT. Examples of valid TRM names are: TRMINMyVeryOwn, TRMINStandard, TRMOUTMyVeryOwn, and TRMOUTStandard.  
  
 The type library or structure can contain multiple TRM definitions, but you should include only one TRM for each direction (that is, one TRMIN and one TRMOUT) in the COMTIContext parameter in a single method call. For example, in Visual Basic each COMTIContext array is declared as a single dimension dynamic array of variants (that is, the number of occurrences is not specified).  
  
 If you define multiple TRMs for the same direction, the TI run time uses only the first TRM it encounters in the context array. (In some circumstances, the first TRM encountered might not always be the first one that you added to the context array). The TI run time ignores the remaining TRMs in the array until the TRM in use is destroyed. To ensure that the TI run time uses the correct TRM, do not add multiple TRMs intended for the same direction to a context array.  
  
> [!NOTE]
>  The client application that manipulates the Context array must be able to access the appropriate file at run time. If you are using Visual Basic6.0, the application must be able to access COMTIContext.dll. If you are using Visual Basic .NET, the application must able to access Microsoft.HostIntegration.TI.ClientContext.dll.  
  
> [!NOTE]
>  When you use Visual Basic .NET, the data structure used as a custom TRM must be associated to a parameter within the assembly. Therefore, you must create a dummy method within the assembly, a parameter assigned to the method, and the data structure to be used as the TRM. Failure to do so prevents you from referencing the structure within the Visual Basic .NET application. Associating a UDT to a method was not required in Visual Basic 6.0 because Visual Basic 6.0 allowed referencing of UDTs not associated with methods.  
  
## See Also  
 [Transaction Request Messages](../HIS2010/transaction-request-messages1.md)   
 [How to Pass a Custom TRM](../HIS2010/how-to-pass-a-custom-trm1.md)