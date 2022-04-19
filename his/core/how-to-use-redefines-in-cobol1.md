---
description: "Learn more about: How to Use REDEFINES in COBOL"
title: "How to Use REDEFINES in COBOL1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f419b19a-ed95-4c59-a7ec-d216379b85e5
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Use REDEFINES in COBOL
The COBOL import process in Transaction Integrator (TI) Project recognizes the REDEFINES clause in a data description entry and correctly associates the redefining entries with the redefined entry. You must select one of the redefined or redefining clauses as the entry that represents the data that will be transmitted.  
  
 The redefining entries can use less space than the redefined entry. If you select a redefining entry that is smaller than the redefined entry, TI Project automatically adds filler so that the data will correctly overlay the data description when it is sent to the host. If the redefining entry represents a table with multiple fields, the last field contains the filler.  
  
 The following COBOL example shows a REDEFINES clause. The redefining clause was selected during import:  
  
```  
01 CUSTOMER-DATA.  
   05 CUSTOMER-ID                          PIC X(10).  
   05 CUSTOMER-ID-PARTS REDEFINES CUSTOMER-ID.  
      10 LOCATION                          PIC X(3).  
      10 NAME-ABREV                        PIC X(5).  
  
```  
  
 The resulting method that is imported is:  
  
```  
CreateCustomerID(strLocation As String, strNameAbrev As String)  
  
```  
  
 The COBOL generated for this method is:  
  
```  
01 CREATECUSTOMERID-INPUT-AREA.  
   05 LOCATION              PIC X(3).               INPUT  
   05 NAME-ABREV            PIC X(5).               INPUT  
   05 FILLER                PIC X(2).               INPUT  
  
```  
  
 The FILLER is added to the CUSTOMER-ID redefined area. When this FILLER occurs at the end of send or receive buffers, for performance reasons it is not sent.  
  
 The following is an example of Visual Basic code that calls this method:  
  
```  
Dim objCustomer As Object  
Dim strLocation As String  
Dim strNameAbrev As String  
  
strLocation = "101"  
strNameAbrev = "SPORT"  
  
'create an instance of the invoicing object  
On Error GoTo ErrorHandler1  
Set objCustomer = CreateObject("Customer.Invoicing.1")  
  
'invoke the CreateCustomerID method  
On Error GoTo ErrorHandler2  
objCustomer.CreateCustomerID strLocation, strNameAbrev  
```  
  
## See Also  
 [Filler](../core/filler1.md)
