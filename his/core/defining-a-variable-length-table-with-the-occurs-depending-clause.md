---
title: "Defining a Variable-length Table with the OCCURS DEPENDING Clause | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02ef3bb4-47a2-493e-877e-8466df279725
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Defining a Variable-length Table with the OCCURS DEPENDING Clause
In COBOL, you can use the OCCURS DEPENDING ON syntax to define a variable-length table in a data declaration. The storage for a variable-length table is dynamic, depending on the value in the length specifier variable. The amount of data passed is also dependent on the value in the length specifier variable: Only the number of elements specified are sent or received. The length specifier variable for a variable-length table must be a numeric type, and its direction must match the direction of the variable-length table it controls.  
  
 When you import COBOL into Transaction Integrator (TI) Project, and you specify variable-length tables as recordsets, the variable-length tables automatically become arrays or recordset objects whose size is limited by another parameter. The length specifier is exposed on the Automation side as a parameter and must be correctly set when the parameter is being sent to the host application.  
  
 To manually indicate that a parameter in a method is the length specifier for an array, first define the length specifier parameter, and then define the array or recordset parameter:  
  
 In the parameter property class to be defined as an ODO array, use the Designer to  select the **Is Array** property. After **IsArray** is selected, the **Array Dimensions** and **Occurs depending on** property becomes available. Define the array's dimensions using the **Array Dimensions** property. Assign the ODO index to the parameter defined as the ODO array. Select the index by expanding the property **Occurs depending on**.  
  
 You can also manually indicate that a parameter in a method is the length specifier for a recordset parameter.  
  
 Follow the same steps as defined earlier; however, change the data type of the parameter from a simple data type to a recordset.  
  
 The following COBOL code shows a variable-length table:  
  
```  
01 CUSTOMER-DATA.  
   05 CUSTOMER-NUMBER                 PIC 9(9).  
   05 LAST-NAME                       PIC X(20).  
   05 FIRST-NAME                      PIC X(20).  
   05 INVOICE-COUNT                   PIC 9(7) COMP-3.  
   05 INVOICES OCCURS 50 TIMES DEPENDING ON INVOICE-COUNT.  
      10 INVOICE-NUMBER               PIC 9(10).  
      10 INVOICE-DATE                 PIC 9(7) COMP-3.  
      10 INVOICE-AMOUNT               PIC S9(13)V9(2) COMP-3.  
      10 INVOICE-DESCRIPTION          PIC X(40).  
  
```  
  
 The following is the method that is created when the previous COBOL is imported:  
  
```  
SendInvoices(lCustomerNo As Long, strLastName As String, strFirstName As String _  
    , lcInvoices As Long) As Object  
  
```  
  
 The following is an example of Microsoft® Visual Basic® code that calls an imported method:  
  
```  
Dim objCustomer As Object   'Uses late binding  
Dim objInvoices As ADODB.Recordset  
Dim lCustomerNumber As Long  
Dim iRow As Integer  
Dim iCol As Integer  
Dim strLastName As String  
Dim strFirstName As String  
  
'create an instance of the invoicing object  
On Error GoTo ErrorHandler1  
Set objCustomer = CreateObject("Customer.Invoicing.1")  
  
lCustomerNumber = CLng(txtCustomerNumber)  
  
'invoke the GetInvoices method  
On Error GoTo ErrorHandler2  
Set objInvoices = objCustomer.GetInvoices(lCustomerNumber _  
    , strLastName, strFirstName)  
'  
' Transfer the Recordset data to a variant array in a single operation.  
' This is efficient, but may not be suitable for larger Recordsets.  
'  
Dim Data As Variant  
  
Data = objInvoices.GetRows  
grdInvoices.Rows = UBound(Data, 2) + 1  
grdInvoices.Cols = UBound(Data, 1) + 1  
  
```