---
description: "Learn more about: How to Import a TI Component"
title: "How to Import a TI Component2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Import a TI Component
You can import the methods, recordsets, and user-defined types from an existing component library to another component library. This is useful, for example, if you want to build a new component library based on an existing one.  
  
 Imported methods, recordsets and user-defined types are added to those of the library into which they are imported. If duplicate method names exist between the two libraries, you are asked to supply a new name for a method before it is imported. Duplicate recordset names are allowed unless columns within the recordsets do not match, or Automation data types and associated COBOL data types within a column do not match. In this case, you are asked to supply a new name for a recordset before it is imported.  
  
### To Import a TI Component  
  
1.  In the console tree of HIS Designer, right-click the icon for your component library's interface.  
  
2.  Point to **Import**, and then click **Component Library**.  
  
3.  In the **Insert Component Library** dialog box, locate and click the TI component library (the .tlb file) that you want to import.  
  
4.  Click **Open**.  
  
## See Also  
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components2.md)   
 [Transaction Integrator User's Guide](../core/transaction-integrator-user-s-guide2.md)
