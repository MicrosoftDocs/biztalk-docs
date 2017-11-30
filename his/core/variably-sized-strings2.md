---
title: "Variably Sized Strings2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 978c233f-2924-480b-b073-9500ec0f2988
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Variably Sized Strings
When the last input parameter or the last output parameter in a method is a string, that string can be variably sized. Its size can vary from 0 to the maximum number of bytes specified for its length. When the return value is a string and it is positioned after all other output parameters, it can be the variably sized final output field.  
  
 The string must be sent or received last if it is to be variably sized. Otherwise, there is no reliable way to determine the end of a variably sized string and the next data item in the buffer. The logic of the host application sends only the data for the part of the string that is needed.  
  
 COBOL never sets the variably sized option for strings. To set this property manually, set the **Variable Sized Final Field** property to be variable. The property **Variable Sized Final Field** is subdivided into two parts by direction. Set the direction you want to true.  
  
 The following COBOL example has as its last data item a large string that could be optimized by sending only the size of the string:  
  
```  
01 CUSTOMER-DATA.  
   05 CUST-HEADER.  
      10 CUSTOMER-NUMBER              PIC 9(9).  
      10 LAST-NAME                    PIC X(20).  
      10 FIRST-NAME                   PIC X(20).  
   05 COMMENTS                        PIC X(4096).  
  
```  
  
 When imported, this COBOL code creates the following method:  
  
```  
CustomerInformation(lCustomerNo As Long,_  
                    strLastName As String,_  
                    strFirstName As String,-  
                    strComments As String)  
  
```  
  
 The following Visual Basic code calls the method:  
  
```  
Dim objCustomer As Object  
    Dim lCustomerNo As Long  
    Dim strLastName As String  
    Dim strFirstName As String  
    Dim strComments As String  
  
    lCustomerNo = 100231  
  
    'create an instance of the invoicing object  
    On Error GoTo ErrorHandler1  
    Set objCustomer = CreateObject("Customer.Invoicing.1")  
  
    'invoke the SetInvoices method  
    On Error GoTo ErrorHandler2  
    objCustomer.CustomerInformation lCustomerNo, strLastName _  
        , strFirstName, strComments  
  
```