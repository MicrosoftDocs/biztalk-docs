---
title: "TI Application Cannot Reference FILLER2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02987062-5227-4752-ba88-7fdb528ee646
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TI Application Cannot Reference FILLER
There are at least three possible causes for why the application cannot reference FILLER data:  
  
- Mainframe or COBOL specifics.  
  
- Automation specifics.  
  
- Procedure using TI Project.  
  
  The following provides details of these three causes.  
  
## Mainframe or COBOL Specifics  
 When a FILLER keyword is encountered in the import process, the Transaction Integrator (TI) run-time environment adjusts the offset for the position of the data that follows the filler in a send or receive buffer by the length of the filler. This leaves untranslated gaps in the buffers that are sent to (or received from) the host and allows your data to overlay correctly onto the data declaration that describes it.  
  
## Automation Specifics  
 The Automation method does not reference the filler data description entries.  
  
## Procedure Using TI Project  
 The filler that is at the start of a data declaration is associated with a method, recordset, datatable, user-defined type (UDT), or .NET structure. You can view or change filler that is associated with a method from the **Advanced** tab of the method's properties page. To view or change a filler that is associated with a method, recordset, or UDT, right-click the method, recordset, or UDT, and then click **Properties**.  
  
 Filler that follows a data description entry is associated with the data description entry (or parameter for methods, column for recordsets, or member for UDTs). You can view or change filler that is associated with a parameter, column, or member from the **COBOL Definitions** tab of the parameter, column, or member properties. When filler follows the data description entry that you have specified as the return value, you can view or change that filler from the **COBOL Definitions** tab of the method's properties.  
  
 The following example shows a COBOL data declaration that uses FILLER:  
  
```  
01 CUSTOMER-DATA.  
   05 CUSTOMER-INFO.  
      10 LAST-NAME                PIC X(20).  
      10 FIRST-NAME               PIC X(20).  
      10 FILLER                   PIC X(12).  
   05 DEMOGRAPHICS.  
      10 DEMO-AGE                 PIC 999.  
      10 DEMO-INCOME              PIC S9(9)V99 COMP-3.  
      10 DEMO-SEX                 PIC X.  
      10 DEMO-MSTATUS             PIC X.  
      10 FILLER                   PIC X(40).  
  
```  
  
 The resulting method is:  
  
```  
CustomerDemographics(strLastName As String, strFirstName As String, iAge As Integer _  
    , curIncome As Currency, strSex As String, strMStatus As String)  
  
```  
  
 The following is an example of the Visual Basic code that calls the method:  
  
```  
Dim objCustomer As Object  
    Dim strLastName As String  
    Dim strFirstName As String  
    Dim iAge As Integer  
    Dim curIncome As Currency  
    Dim strSex As String  
    Dim strMStatus As String  
  
    strLastName = "Doe"  
    strFirstName = "John"  
  
    'create an instance of the invoicing object  
    On Error GoTo ErrorHandler1  
    Set objCustomer = CreateObject("Customer.Invoicing.1")  
  
    'invoke the SetInvoices method  
    On Error GoTo ErrorHandler2  
    objCustomer.CustomerDemographics strLastName, strFirstName _  
        , iAge, curIncome, strSex, strMStatus  
```  
  
## See Also  
 [Filler](../core/filler1.md)