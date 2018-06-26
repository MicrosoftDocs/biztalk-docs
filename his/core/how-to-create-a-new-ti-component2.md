---
title: "How to Create a New TI Component2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c0e6198-69b7-4ca3-9480-ca24eec46a4a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Create a New TI Component
Use Host Integration Server Designer (HIS Designer) to create a new Transaction Integrator (TI) component and populate it with methods.  
  
### To create a new TI component  
  
1. Start HIS Designer.  
  
2. On the **File** menu, click **New**.  
  
3. Type a library name for the new TI component library.  
  
4. Type a name for the TI component library's interface.  
  
5. Type a version number for the component library.  
  
    The number to the left of the decimal point is the major version number. The number to the right of the decimal point is the minor version number.  
  
6. Click the type of remote environment (RE) that your component will use.  
  
7. Click the component library's Transaction support property.  
  
    In this case, you are deciding whether the component will support ACID (atomic, consistent, isolated, durable) transactions that each support two-phase commit (2PC). If you click **Does not support transactions**, your TI component will still support mainframe transactions in mainframe transaction programs (TP).  
  
8. If you are providing Help for your application, type the context ID for the first topic in the **Starting Help Context ID** box.  
  
9. Click **OK**.  
  
     You will now see folders and icons for **Interface**, **Methods**, **Recordsets**, and **User-Defined Types**.  
  
     **To add a method to the interface**  
  
   - In the console tree of HIS Designer, right-click **Methods**, point to **Insert Method**, and then click a data type that represents the return value.  
  
     **To add a parameter to a method**  
  
   - In the console tree of HIS Designer, right-click the name of the method, point to **Insert Parameter**, and then click a data type.  
  
     **To add a recordset to the interface**  
  
   - In the console tree of HIS Designer, right-click **Recordsets**, and then click **Insert Recordset**.  
  
     **To add a member to the recordset**  
  
   - In the console tree of HIS Designer, right-click the name of the recordset, point to `Insert Recordset Member`, and then click a data type.  
  
     **To add a user-defined type to the interface**  
  
   - In the console tree of HIS Designer, right-click **User-Defined Types**, and then click **Insert User-Defined Type**.  
  
     **To add a member to the user-defined type**  
  
   - In the console tree of HIS Designer, right-click the name of the User-Defined Type, point to **Insert User-Defined Type Member**, and then click a data type.  
  
## See Also  
 [Creating and Managing TI Components](../core/creating-and-managing-ti-components2.md)   
 [Transaction Integrator User's Guide](../core/transaction-integrator-user-s-guide2.md)