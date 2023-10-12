---
description: "Learn more about: How to Import COBOL into a TI Component"
title: "How to Import COBOL into a TI Component2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Import COBOL into a TI Component
You can import COBOL source code to define the Automation interface of a new Transaction Integrator (TI) component library. To do so, use the TI COBOL wizard to create one method at a time. The COBOL wizard initially imports an entire source file for a mainframe transaction program (TP). As you step through the wizard, you extract the data declarations that describe input sent to, and output received from, the mainframe TP. These data declarations are used to define your TI component library. All other content in the source file is ignored.  
  
 As you develop your TI application, you can continue to use the COBOL wizard to make adjustments to a component definition. For example, you can add a parameter to a method to incorporate updates that have been made to the COBOL source code on the mainframe. To adjust a component definition, you can re-run the COBOL wizard to replace a method or a recordset in your component definition. Before replacing an existing method or recordset, you must unlock the method or recordset. Component definitions are locked by default to protect against unintended changes.  
  
### To import COBOL into a TI component  
  
1.  In the console tree of Host Integration Server Designer (HIS Designer), right-click the icon for your component library's interface.  
  
2.  Point to **Import**, and click **COBOL Wizard**.  
  
3.  Follow the instructions on the screen.  
  
     The COBOL wizard steps you through the process of importing the COBOL source code that you want.  
  
### To unlock a method or record set  
  
1.  Start HIS Designer, and right-click the method or recordset.  
  
2.  Click **Unlock**.  
  
## See Also  
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components2.md)   
 [Transaction Integrator User's Guide](../core/transaction-integrator-user-s-guide2.md)
