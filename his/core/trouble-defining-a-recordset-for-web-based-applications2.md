---
title: "Trouble Defining a Recordset for Web-Based Applications2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d0d05a5-cc3a-4b61-bf76-b190c4e76ad4
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Trouble Defining a Recordset for Web-Based Applications
In TI, a *recordset* consists of tabular data defined in COBOL source code on the mainframe. Tabular data is defined by a group item containing an OCCURS clause in the COBOL data area. When you import a COBOL data area into TI Designer, the following COBOL-to-Automation conversions take place:  
  
- The COBOL data area defines the parameters of the newly created method and the members of any recordsets.  
  
- The group item that defines the table (contains the OCCURS clause) is represented as both the type definition of the method's recordset and a method parameter.  
  
- Other group items are represented as method parameters.  
  
- Elemental data items (definitions of the table fields) are represented as the recordset's members.  
  
  The following COBOL data area describes the type library for a Web-based application that uses a CICS LINK remote environment. The application returns information on up to six accounts for each customer name and matching PIN entered as input.  
  
```  
01         DFHCOMMAREA.  
*                    ACCTINFO IS (INPUT, OUTPUT)  
           O5        ACCTINFO OCCURS 6 TIMES.  
                     10 ACCOUNTNUMBER                       PIC X(6).  
                     10 ACCOUNTTYPE                         PIC X(20).  
                     10 CURRENTBALANCE                      PIC S9(13)V9(2) COMP-3.  
  
                     10 INTERESTBEARING                     PIC S9(4) COMP.  
                     10 INTERESTRATE                        COMP-1.  
                     10 MONTHLYSVCCHG                       PIC S9(13)V9(2) COMP-3.  
  
*                    NAME IS (INPUT, OUTPUT)  
                     05                                     NAMEPIC X(30).  
*                    PIN IS (INPUT, OUTPUT)  
                     05                                     PIN PIC X(10).  
  
```  
  
 When imported into TI Designer, the data area's group items are treated as the parameters of the newly created method. However, because of Remote Data Service (RDS) requirements for Web-based applications, the group item that defines the table must be defined as the method's return value, not as a method parameter. To define the method correctly, you must manually redefine this group item (ACCTINFO in the previous example) as a return value.  
  
 Before you import the COBOL data area, note the number of rows specified in the OCCURS clause. After you have imported the COBOL data area, use the following procedure to define a recordset for Web-based applications.  
  
#### To define a recordset for a Web-based application  
  
1. Start TI Designer.  
  
2. In the console tree, double-click the **Recordsets** folder to verify that TI Designer created the type definition of the recordset. The type definition's name is taken from the group item that defined the table in the COBOL source code.  
  
3. Double-click the **Methods** folder, and click the method's name. Verify that the recordset parameter is displayed in the details pane. The parameter name should match the name of the recordset's type definition.  
  
4. On the **Edit** menu, click **Unlock** to unlock the method.  
  
5. In the details pane, delete the recordset parameter.  
  
6. Right-click the method, click **Properties**, and then click the **Automation Definition** tab.  
  
7. Click the name of the recordset's type definition in the **Return Type** box.  
  
8. Click the **Recordsets** tab.  
  
9. In the **Group-Item Maximum** box, type the number of rows specified in the COBOL source code, and then click **OK**.  
  
   For detailed information about recordsets, see the ActiveX Data Objects (ADO) and Remote Data Service (RDS) documentation included when you installed Microsoft Data Access Components (MDAC).