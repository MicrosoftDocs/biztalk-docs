---
title: "How to Export COBOL from a TI Component1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ffd7732-6980-443a-9a9f-9e058f4f17ac
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Export COBOL from a TI Component
You can use a component definition to generate COBOL syntax for the data declarations that describe input sent to, and output received from, the mainframe transaction program (TP). The generated COBOL syntax is saved in a text file. The file's contents are not an actual program, but data declarations. The file contains data only, not logic, and is intended to serve as a guideline, for example, for code that can be incorporated into a mainframe TP.  
  
### To export COBOL from a TI Component  
  
1.  In the console tree of HIS Designer, right-click the icon for your component library's interface.  
  
2.  Point to **Export**, and then click **Generate COBOL Declarations**.  
  
     If you are exporting from a new (unsaved) component library, you are prompted to save the library.  
  
3.  Click **OK**.  
  
     The **Save File As** dialog box appears.  
  
4.  Fill in the dialog box and then click **Save**.  
  
     Transaction Integrator (TI) displays the text file in Notepad for you to view.  
  
## See Also  
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components.md)   
 [Transaction Integrator User's Guide](../core/transaction-integrator-user-s-guide.md)