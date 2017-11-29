---
title: "CICS LU6.2 User Data2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 779dfac4-c27c-40de-bdd4-8d7be613917f
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# CICS LU6.2 User Data
The CICS LU6.2 User Data programming model provides direct invocations and data exchanges between TI and the server TP. No other communication components are required with this model.  
  
 The following figure summarizes the workflow occurring between the client, the default CICS Mirror Transaction, and the mainframe transaction program. The numbers in parentheses indicate the approximate order in which events occur. A more detailed description of the events follows the figure.  
  
 ![](../core/media/his-ti14.gif "his_ti14")  
Transaction Integrator sending and receiving LU 6.2 or TCP/IP from the mainframe transaction program  
  
## Summary workflow diagram for the CICS LU6.2 User Data programming model  
 The CICS LU6.2 User Data programming model works as follows:  
  
1.  An application invokes a method in a TI component configured in either Component Services or the .NET Framework.  
  
2.  The TI runtime calls the TI Automation proxy.  
  
3.  If the application is a COM+ component, the TI Automation proxy:  
  
    1.  Reads in the type library created previously by the TI Designer.  
  
    2.  Maps the automation data types to COBOL data types.  
  
     If the application is a .NET assembly, the TI Automation proxy:  
  
    1.  Reads in the assembly and metadata created previously by the TI Designer.  
  
    2.  Maps the .NET Framework data types to COBOL data types.  
  
     The TI Automation proxy then:  
  
    1.  Calls the conversion routines to convert the application data to mainframe COBOL types.  
  
    2.  Builds the flattened data stream buffer that represents the COBOL declaration or copybook.  
  
    3.  Passes the message to the SNA transport component.  
  
4.  The TI proxy sends the TP invocation request specified by the TI component method to the server TP by using the LU6.2 protocol. In this message, TI sends the TRANID of the server TP that the method is invoking.  
  
5.  TI and the server TP communicate directly by issuing APPC or Common Programming Interface for Communications (CPI-C) verbs to receive and send the input and output fields, respectively.  
  
6.  If necessary, the server TP issues the appropriate verbs to implement Sync Level 2 properties and 2 phase commit.  
  
7.  The mainframe TP closes the socket.  
  
8.  The TI Automation proxy receives the reply data and processes the reply. The TI Automation proxy:  
  
    1.  Receives the message from the SNA transport component.  
  
    2.  Reads the message buffer  
  
     If the application is a COM+ component, the TI Automation proxy:  
  
    1.  Maps the COBOL data types to the automation data.  
  
    2.  Calls the conversion routines to convert the mainframe COBOL types to the application data.  
  
     If the application is a .NET assembly, the TI Automation proxy:  
  
    1.  Maps the COBOL data types to the .NET Framework data types.  
  
    2.  Calls the conversion routines to convert the mainframe COBOL types to the application data.  
  
9. The TI runtime sends the converted data back to the COM or .NET Framework application that invoked the method.  
  
 [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] includes sample code showing how to implement the CICS LU6.2 User Data programming model. The sample code is located at **\\***installation directory***\SDK\Samples\AppInt**. Start Microsoft Visual Studio, open the tutorial you want to use, and follow the instructions in the **Readme**.  
  
## See Also  
 [Transaction Integrator Components](../core/transaction-integrator-components.md)   
 [Configure Host Environment and Programming Model Wizard Page](../Topic/Configure%20Host%20Environment%20and%20Programming%20Model%20Wizard%20Page1.md)   
 [Converting Data Types from Automation to OS/390 COBOL\]](../Topic/Converting%20Data%20Types%20from%20Automation%20to%20OS-390%20COBOL]1.md)   
 [Converting Data Types from OS/390 COBOL to Automation](../Topic/Converting%20Data%20Types%20from%20OS-390%20COBOL%20to%20Automation1.md)   
 [CICS Components](../core/cics-components.md)   
 [TI Runtime](../core/ti-runtime.md)   
 [Choosing the Appropriate Programming Model](../core/choosing-the-appropriate-programming-model.md)   
 [Programming Models](../core/programming-models.md)