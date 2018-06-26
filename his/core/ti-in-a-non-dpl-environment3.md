---
title: "TI in a Non-DPL Environment3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9e72743-8cf7-4600-b440-117935c2903c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TI in a Non-DPL Environment
A non-linked environment (that is, a non-DPL environment) is one that does not use IBM Distributed Program Link (DPL). You can use TI to invoke a mainframe transaction program (TP) that uses the **EXEC CICS RECEIVE INTO** and **EXEC CICS SEND FROM** COBOL commands. These two COBOL commands are useful when you want a CICS TP to take on SNA (APPC/LU 6.2) conversation responsibilities and therefore bypass the Mirror TP. In other words, the **EXEC CICS RECEIVE INTO** and **EXEC CICS SEND FROM** COBOL commands are most often used in a non-linked environment to transfer data to and from an LU of type 6.2 (APPC).  
  
 TI supports the LU 6.2 model for both linked and nonlinked environments. You can create the following remote environment (RE) types to support each model:  
  
- **CICS Link using LU 6.2**  
  
   Use this in an IBM DPL environment that uses the Mirror TP.  
  
- **CICS using LU 6.2**  
  
   Use this in a non-DPL environment that bypasses the Mirror TP.  
  
  Many customers use TI in a non-DPL environment. The only concern is whether terminal logic is embedded with the business logic. When a COBOL TP supports IBM DPL, the presentation logic has already been separated from the business logic, so you probably will not need to modify the COBOL. However, if the TP was written to communicate with a terminal, it is likely that you will need to modify the COBOL code to separate the business logic from the presentation logic.  
  
  For example, the following sample COBOL code shows how to handle unbound recordsets by using the **EXEC CICS RECEIVE INTO** and **EXEC CICS SEND FROM** COBOL commands:  
  
```  
*****************************************************  
* Example showing how to send unbounded recordsets  
* to a client application.  
*****************************************************  
 IDENTIFICATION DIVISION.  
  
 ENVIRONMENT DIVISION.  
  
 DATA DIVISION.  
  
 WORKING-STORAGE SECTION.  
  
* INPUT AREA  
 01  CUSTOMER-INPUT-NUMBER                PIC 9(9).  
  
* OUTPUT AREA  
 01  CUSTOMER-DATA.  
     05  LAST-NAME                        PIC X(20).  
     05  FIRST-NAME                       PIC X(20).  
  
* ONE ROW IN A DATABASE TABLE  
 01  INVOICES.  
     05  INVOICE-NUMBER                   PIC 9(10).  
     05  INVOICE-DATE                     PIC 9(7) COMP-3.  
     05  INVOICE-AMOUNT                   PIC S9(13)V9(2) COMP-3.  
     05  INVOICE-DESCRIPTION              PIC X(40).  
  
 LINKAGE SECTION.  
  
 PROCEDURE DIVISION.  
*  
*   Get the input customer account number from the  
*   client applicaton:  
*  
     MOVE LENGTH OF CUSTOMER-INPUT-NUMBER TO RECEIVE-LENGTH  
     EXEC-CICS RECEIVE INTO(CUSTOMER-INPUT-NUMBER)  
               LENGTH(RECEIVE-LENGTH)  
               END-EXEC.  
*  
*   Do some work; then send the first and last name back:  
*  
     MOVE LENGTH OF CUSTOMER-DATA TO SEND-LENGTH  
     EXEC-CICS SEND FROM(CUSTOMER-DATA)  
               LENGTH(SEND-LENGTH)  
               END-EXEC.  
*  
*   Follow regular data with unbounded table data that  
*   the client application sees as a recordset:  
*  
     MOVE LENGTH OF INVOICES TO SEND-LENGTH  
     PERFORM UNTIL        NO-MORE-INVOICES  
*  
*   Do some work to get the next row:  
*  
     MOVE DB-INVOICE-NUMBER TO INVOICE-NUMBER  
     MOVE DB-INVOICE-DATE   TO INVOICE-DATE  
     MOVE DB-INVOICE-AMOUNT TO INVOICE-AMOUNT  
     MOVE DB-INVOICE-DESC   TO INVOICE-DESCRIPTION  
*  
*   Send the row:  
*  
     EXEC-CICS SEND FROM(INVOICES)  
               LENGTH(SEND-LENGTH)  
               END-EXEC.  
     END-PERFORM.  
  
```  
  
## See Also  
 [Windows-Initiated Processing](../core/windows-initiated-processing2.md)