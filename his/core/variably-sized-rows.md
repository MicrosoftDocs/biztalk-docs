---
title: "Variably Sized Rows1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8db546c0-3768-4ddd-b984-ce2d018a7d36
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Variably Sized Rows
When the last column in a record is a string, the row can be variably sized. Its size can vary between zero and the maximum size specified in the picture clause. When you have variably sized rows, your application must explicitly specify the size of each row before the row is sent.  
  
 The actual size field is not visible on the Automation side. The Transaction Integrator (TI) run-time environment uses Automation services to determine the size of input data. When the TI run-time environment sends data to the host, it automatically sets the actual size field.  
  
 The Import COBOL Wizard never creates a recordset that has variably sized rows. Bring up properties for the recordset that contains the variably sized rows. The **Variable sized rows** property allows user to manually configure this option for a specific recordset. The **Variable sized rows** property offers advanced options. You can specify that the actual row size variable is a half-word or full-word binary. The actual size variable will include itself or will only include the size of the row.  
  
 The following COBOL example shows how the host application sends variably sized rows. The length field is included in the row size:  
  
```  
01  CUSTOMER-DATA.  
    05  CUSTOMER-NUMBER                  PIC 9(9).  
    05  LAST-NAME                        PIC X(20).  
    05  FIRST-NAME                       PIC X(20).  
    05  INVOICE-COUNT                    PIC 9(7) COMP-3.  
    05  INVOICES OCCURS 50 TIMES DEPENDING ON INVOICE-COUNT.  
        10  INVOICE-DATA.  
            15  INVOICE-ROW-SIZE         PIC S9(4) COMP.  
             15  INVOICE-NUMBER           PIC 9(10).  
             15  INVOICE-DATE             PIC 9(7) COMP-3.  
             15  INVOICE-AMOUNT           PIC S9(13)V9(2) COMP-3.  
         10  INVOICE-DESCRIPTION          PIC X(4096).  
.  
.  
.  
            MOVE LENGTH OF CUSTOMER-DATA TO SEND-LENGTH.  
            SUBTRACT LENGTH OF INVOICES FROM SEND-LENGTH.  
            EXEC-CICS SEND FROM(CUSTOMER-DATA)  
                           LENGTH(SEND-LENGTH)  
                           END-EXEC.  
  
            PERFORM VARYING ROW FROM 1 BY 1 UNTIL ROW > INVOICE-COUNT  
                INSPECT INVOICE-DESCRIPTION TALLYING INVOICE-ROW-SIZE  
                    FOR CHARACTERS BEFORE INITIAL '   '  
                ADD LENGTH OF INVOICE-DATA TO INVOICE-ROW-SIZE  
                EXEC-CICS SEND FROM(INVOICE-ROW-SIZE)  
                               LENGTH(2)  
                               END-EXEC  
                EXEC-CICS SEND FROM(INVOICES(ROW))  
                               LENGTH(INVOICE-ROW-SIZE)  
                               END-EXEC  
            END-PERFORM.  
  
```  
  
 The following COBOL example shows how the host application sends variably-sized rows. The length field is not included in the row size:  
  
```  
       01  CUSTOMER-DATA.  
          05  CUSTOMER-NUMBER                  PIC 9(9).  
          05  LAST-NAME                        PIC X(20).  
          05  FIRST-NAME                       PIC X(20).  
          05  INVOICE-COUNT                    PIC 9(7) COMP-3.  
          05  INVOICE-ROW-SIZE                 PIC S9(4) COMP.  
         05  INVOICES OCCURS 50 TIMES DEPENDING ON INVOICE-COUNT.  
             10  INVOICE-DATA.  
                  15  INVOICE-NUMBER           PIC 9(10).  
                  15  INVOICE-DATE             PIC 9(7) COMP-3.  
                  15  INVOICE-AMOUNT           PIC S9(13)V9(2) COMP-3.  
              10  INVOICE-DESCRIPTION          PIC X(4096).  
.  
.  
.  
            MOVE SIZE OF CUSTOMER-DATA TO SEND-LENGTH.  
            SUBTRACT LENGTH OF INVOICES FROM SEND-LENGTH.  
            SUBTRACT LENGTH OF INVOICE-ROW-SIZE FROM SEND-LENGTH.  
            EXEC-CICS SEND FROM(CUSTOMER-DATA)  
                           LENGTH(SEND-LENGTH)  
                           END-EXEC.  
  
            PERFORM VARYING ROW FROM 1 BY 1 UNTIL ROW > INVOICE-COUNT  
                INSPECT COMMENTS TALLYING INVOICE-ROW-SIZE  
                    FOR CHARACTERS BEFORE INITIAL '   '  
                ADD LENGTH OF INVOICE-DATA TO INVOICE-ROW-SIZE  
                EXEC-CICS SEND FROM(INVOICE-ROW-SIZE)  
                               LENGTH(LENGTH OF INVOIVE-ROW-SIZE)  
                               END-EXEC  
  
                EXEC-CICS SEND FROM(INVOICES(ROW))  
                               LENGTH(INVOICE-ROW-SIZE)  
                               END-EXEC  
            END-PERFORM.  
  
```  
  
## See Also  
 [Defining a Variable-length Table with the OCCURS DEPENDING Clause](../core/defining-a-variable-length-table-with-the-occurs-depending-clause.md)   
 [Variably Sized Strings](../core/variably-sized-strings.md)   
 [Bounded Final Fields](../core/bounded-final-fields.md)