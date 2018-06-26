---
title: "TI Runtime2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2036d8af-b2ad-409b-bb99-70fc24040796
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TI Runtime
The TI run-time environment is a specialized run-time environment started by Windows or a requesting IBM application program when the application contains a TI component. For each TI component you create, the TI run-time environment provides the Automation server interface and communicates with the mainframe programs. The TI run-time environment does not have a visible user interface.  
  
 As a generic proxy for the mainframe or AS/400 computer, the TI run-time environment intercepts object method calls and redirects those calls to the appropriate mainframe program. It also handles the return of all output parameters and return values from the mainframe. When TI intercepts the method call, it converts and formats the method's parameters from the representation understandable by the Windows Server platform into the representation understandable by host transaction programs (TPs).  
  
 The TI object that exposes the functionality of a mainframe TP as an interface method. It can expose all of the TP's functionality. A client application calls the TI object to invoke the mainframe TP, pass parameters, and return results.  
  
 At run time, the TI run-time environment intercepts method invocations from a client application for a TI component library and provides the actual parameter conversion and formatting.  
  
 The client application can be any .NET Framework application that calls a TI Automation server to invoke a mainframe TP. The client application provides the presentation layer for the application or data. It can be anything capable of calling a COM+ or .NET Framework object, including an Active Server Page (ASP), a Visual Basic application, or even a Microsoft Office application. The client application that uses a TI object can be running on computer that is running Windows Server, any later version of Windows, or any other operating system that supports the .NET Object Model. .NET is language-independent, so developers can build their client application by using the languages and tools with which they are most familiar, including Microsoft Visual Basic®, Visual Basic for Applications, Microsoft C#®, Microsoft Visual C++®, Microsoft Visual J++™, Delphi, Powerbuilder, and Microfocus Object COBOL. The client application can then easily make calls to the TI object.  
  
 Then the TI run-time environment sends and receives the method calls to and from (in and out of) the appropriate mainframe TP. TI uses the TI component library created in TI Designer at design time to transform the parameter data that is passed between the TI Automation server and the mainframe TP. TI also integrates with Microsoft Distributed Transaction Coordinator (DTC) to provide two-phase commit (2PC) transaction support in SNA networks.  
  
 The TI run-time environment uses the information in the TI object (.dll) and the associated RE to:  
  
- Activate the TP on the mainframe in the RE.  
  
- Pass the parameters specified by the TI component to the TP on the mainframe by way of the associated RE.  
  
- Run the TP.  
  
- Return the results of the TP to the .NET application TI object, which in turn returns the results to the client application that called it.  
  
  This The TI runtime environment provides the proxy that the TI object uses to invoke the mainframe TP. The TI run-time environment provides these functions:  
  
- Translates between Automation and COBOL data types.  
  
- Translates messages to and from the mainframe.  
  
- Provides a generic object for .NET, the behavior of which is described by a TI object (.dll) for a specific instance.  
  
## See Also  
 [Programming Models](../core/programming-models2.md)   
 [Transaction Integrator Components](../core/transaction-integrator-components1.md)