---
title: "Bounded Final Fields1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ddc839de-ad90-42f9-8660-5d9784dc0cda
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Bounded Final Fields
When the last input or the last output parameter in a method is an array or recordset, that parameter can be bounded. Its size can vary from 0 to the maximum number of elements or rows specified. The array or recordset must be last to be bounded. Otherwise, there is no reliable way to determine the end of a bounded array or recordset and the beginning of the next field in the buffer. The host application must take care of sending the truncated table.  
  
 The Automation client handles this option automatically. The Transaction Integrator (TI) run-time environment sends a truncated amount of data based on the Automation bounds and detects the truncated data and creates the appropriate Automation type when data is received.  
  
 The Import COBOL Wizard never sets the bounded option for arrays or recordsets. To set this manually for the final parameter in a method, use the Designer to assign a value to the property **Maximum Occurrence**. This field defines the maximum number of rows the recordset may contain. On the method containing the recordset, set the property **Variable Sized Final Field** to true by direction to make the recordset bounded.  
  
 If the method contains a recordset that is unbounded, you cannot also specify a bounded or variably-sized final field for that direction. For example, if Parameter1 is an output parameter, and it is an unbounded recordset, the final output parameter cannot be a bounded array or recordset or variably-sized string. When the return value is positioned after all other output parameters, the return value can be the bounded final output field.  
  
 The following COBOL example sends only some of the rows in a recordset:  
  
```  
01  INVOICE-COUNT                        PIC S9(4) COMP.  
01  CUSTOMER-DATA.  
    05  CUSTOMER-NUMBER                  PIC 9(9).  
    05  LAST-NAME                        PIC X(20).  
    05 INVOICES OCCURS 50 TIMES.  
               10  INVOICE-NUMBER               PIC 9(10).  
               10  INVOICE-DATE                 PIC 9(7) COMP-3.  
               10  INVOICE-AMOUNT               PIC S9(13)V9(2) COMP-3.  
.  
.  
.  
            MOVE SIZE OF CUSTOMER-DATA TO SEND-LENGTH.  
            SUBTRACT LENGTH OF INVOICES FROM SEND-LENGTH.  
            EXEC-CICS SEND FROM(CUSTOMER-DATA)  
                           LENGTH(SEND-LENGTH)  
                           END-EXEC.  
            PERFORM VARYING I FROM 1 BY 1 UNTIL I = INVOICE-COUNT  
                COMPUTE SEND-LENGTH = LENGTH OF INVOICE-NUMBER +  
                                      LENGTH OF INVOICE-DATE +  
                                      LENGTH OF INVOICE-AMOUNT  
                EXEC-CICS SEND FROM(INVOICES(I))  
                               LENGTH(SEND-LENGTH)  
                               END-EXEC.  
            END-PERFORM.  
  
```