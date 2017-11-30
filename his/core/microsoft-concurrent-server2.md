---
title: "Microsoft Concurrent Server2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c44192e-c482-4d5e-91bc-1bf56864eb53
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Microsoft Concurrent Server
The MSCS transaction (program mscmtics.cbl) samples support both the Standard and the Enhanced Listener. The transaction program can be started by either the Enhanced or Standard Listener.  
  
 Each listener passes a unique transaction initiation message (TIM) to the transaction program when the Concurrent Server is started. The Standard Listener formats and passes the TIM shown in the following code sample. The length of this TIM is 72 bytes.  
  
```  
01  TRANSACTION-INITIATION-MESSAGE.   
    05  GIVE-TAKE-SOCKET    PIC 9(8) COMP.  
    05  LSTN-NAME           PIC X(8).  
    05  LSTN-SUBNAME        PIC X(8).  
    05  CLIENT-IN-DATA      PIC X(35).  
    05  FILLER              PIC X(1).  
    05  SOCKADDR-IN-PARM.  
        15 SIN-FAMILY       PIC 9(4) COMP.  
        15 SIN-PORT         PIC 9(4) COMP.  
        15 SIN-ADDRESS      PIC 9(8) COMP.  
        15 SIN-ZERO         PIC X(8).  
```  
  
 The Enhanced Listener formats and passes the TIM shown in the following code sample. The length of this TIM is 189 bytes.  
  
```  
01  TRANSACTION-INITIATION-MESSAGE.   
    05  GIVE-TAKE-SOCKET    PIC 9(8) COMP.  
    05  LSTN-NAME           PIC X(8).  
    05  LSTN-SUBNAME        PIC X(8).  
    05  CLIENT-IN-DATA      PIC X(35).  
    05  FILLER              PIC X(1).  
    05  SOCKADDR-IN-PARM.  
        15 SIN-FAMILY       PIC 9(4) COMP.  
        15 SIN-PORT         PIC 9(4) COMP.  
        15 SIN-ADDRESS      PIC 9(8) COMP.  
        15 SIN-ZERO         PIC X(8).  
    05  FILLER              PIC X(80).  
    05  DATA-AREA-2-LEN     PIC 9(4) COMP.  
    05  DATA-AREA-2         PIC X(35).  
```  
  
 The mscmtics.cbl sample Concurrent Server can determine whether the Standard or the Enhanced Listener was used by evaluating the length of the TIM received.  
  
 In a scenario where the Enhanced Listener started the Microsoft Concurrent Server, the mscmtics.cbl program looks at the Client-in-data that is contained in the ELM found in the TIM data area-2 field. The Client-in-data contains the name of the CICS Server program to be executed and the length of the request data to be received from the client. The following code sample shows the contents of this data area.  
  
```  
01 CLIENT-IN-DATA                    PIC X(35).  
01 FILLER REDEFINES CLIENT-IN-DATA.  
   05 CID-USERID                     PIC X(8).  
   05 CID-PASSWORD                   PIC X(8).  
   05 CID-LINK-TO-PROG               PIC X(8).  
   05 CID-COMMAREA-LEN               PIC S9(4) COMP.  
   05 CID-DATA-LEN                   PIC S9(8) COMP.  
   05 CID-VERSION                    PIC X.  
      88 CID-VERSION-1               VALUE X'00'.  
      88 CID-VERSION-2               VALUE X'01'.  
   05 CID-FLAGS                      PIC X(2).  
      88 CID-FLAGS-PERSISTENT-NONE   VALUE X'0001'.  
      88 CID-FLAGS-PERSISTENT-OPEN   VALUE X'0002'.  
      88 CID-FLAGS-PERSISTENT-USE    VALUE X'0004'.  
      88 CID-FLAGS-PERSISTENT-CLOSE  VALUE X'0008'.  
   05 CID-RESERVED                   PIC X.  
   05 CID-FORMAT                     PIC X.  
      88 CID-FORMAT-NOTSET           VALUE X'00'.  
      88 CID-FORMAT-MS               VALUE X'01'.  
      88 CID-FORMAT-IBM              VALUE X'02'.  
  
```  
  
## See Also  
 [Standard Transaction Request and Reply Messages](../core/standard-transaction-request-and-reply-messages2.md)   
 [CICS Enhanced Listener Request and Reply Messages](../core/cics-enhanced-listener-request-and-reply-messages2.md)