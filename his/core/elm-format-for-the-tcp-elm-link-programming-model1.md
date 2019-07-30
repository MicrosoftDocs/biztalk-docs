---
title: "ELM Format for the TCP ELM Link Programming Model1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e5cf870-b90e-4f6d-ad2e-6a9a7644cbc6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# ELM Format for the TCP ELM Link Programming Model
This section describes the format and content of the enhanced listener message (ELM) used by the TCP ELM Link programming model.  
  
## ELM Request Message  
 The following table shows the contents of the request message.  
  
|Client in data|  
|--------------------|  
|35|  
  
 Client in data  
 35 bytes of data used by the CICS TCP/IP security exit and passed to the Concurrent Server in the Transaction Integrator metadata (TIM) file.  
  
## Client in data for Microsoft Security Exit format  
 The following code block describes the format of the client in data for the Microsoft security exit.  
  
```  
struct CLIENT_IN_DATA {  
   BYTE    bUserID[8];  
   BYTE    bPassword[8];  
   BYTE    bLinkToName[8];  
   USHORT  usCommareaLen;  
   BYTE    bReserved[9];  
} UNALIGNED;  
```  
  
## Client in data for IBM Security Exit format  
 The following code block describes the format of the client in data for the IBM security exit.  
  
```  
struct CLIENT_IN_DATA2 {  
   BYTE    bSecFlag;  
   BYTE    bPassword[8];  
   BYTE    bUserID[8];  
   BYTE    bLinkToName[8];  
   USHORT  usCommareaLen;  
   BYTE    bReserved[8];  
} UNALIGNED;  
```  
  
## Client in data for COBOL  
 The following code block describes the format of the client in COBOL  
  
```  
01 CLIENT-IN-DATA                       PIC X(35).  
       01 FILLER REDEFINES CLIENT-IN-DATA.  
          05 CID-USERID                 PIC X(8).  
          05 CID-PASSWORD               PIC X(8).  
          05 CID-LINK-TO-PROG           PIC X(8).  
          05 CID-COMMAREA-LEN           PIC S9(4) COMP.  
          05 CID-DATA-LEN               PIC S9(8) COMP.  
          05 CID-VERSION                PIC X.  
          05 CID-FLAG-1                 PIC X.  
          05 CID-FLAG-2                 PIC X.  
          05 CID-RESERVED               PIC X.  
          05 CID-FORMAT                 PIC X.  
```  
  
## Client in data Constants for COBOL  
 The following code block describes the constants for the client in data in COBOL.  
  
 `01 CLIENT-IN-DATA-CONSTANTS.`  
  
 `05 CID-C-VERSION.`  
  
 `10 CID-VERSION-1            PIC X     VALUE X'00'.`  
  
 `10 CID-VERSION-2            PIC X     VALUE X'01'.`  
  
 `05 CID-C-FLAG-1.`  
  
 `10 CID-USE-TICS-WORK-AREA   PIC X     VALUE X'01'.`  
  
 `05 CID-C-FLAG-2.`  
  
 `10 CID-PC-NONE              PIC X     VALUE X'01'.`  
  
 `10 CID-PC-OPEN              PIC X     VALUE X'02'.`  
  
 `10 CID-PC-USE               PIC X     VALUE X'04'.`  
  
 `10 CID-PC-CLOSE             PIC X     VALUE X'08'.`  
  
 `10 CID-NO-OBJ-PERSIST       PIC X     VALUE X'10'.`  
  
 `05 CID-C-FORMAT.`  
  
 `10 CID-FORMAT-NOTSET        PIC X     VALUE X'00'.`  
  
 `10 CID-FORMAT-MS            PIC X     VALUE X'01'.`  
  
 `10 CID-FORMAT-IBM           PIC X     VALUE X'02'.`  
  
## ELM Reply Message  
 The following table shows the contents of the reply message.  
  
|ELM reply msg length|Formatted field length|Formatted field code|*Data*|  
|--------------------------|----------------------------|--------------------------|------------|  
|4|4|1|*0-n*|  
  
> [!NOTE]
>  The formatted field length, formatted field code, and data can be repeated multiple times in a single message.  
  
 ELM reply msg length  
 The total length of the ELM reply message. This length is the sum of all the lengths of the formatted fields that follow in the message and does not include the length of the ELM reply msg length field itself.  
  
 Formatted field length  
 The length of the formatted field.  
  
 The formatted field length is the sum of the combination of the Formatted field code length and the Data length.  
  
 Formatted field code  
 A 1-byte code that describes the information passed from the Concurrent Server back to the client.  
  
 You cannot change the Formatted field code.  
  
 The field codes are specific to the communication handling between the WIP and HIP TCP Transports and the MSCMTICS, MSHIPLNK and TCP Concurrent Server programs.  
  
 Data  
 0 or more bytes of information that is associated with a specific formatted field.  
  
 You may change the information stored in Data. If you change Data, be sure that you also change the TRM Reply and the Formatted Field Length to the new values.  
  
 The length of Data is equal to the formatted field length minus the size of the formatted field code.  
  
## Normal codes  
 The following table shows the meaning of the normal codes.  
  
|Code|Type|Meaning|  
|----------|----------|-------------|  
|0x01|Info|Version ID for Microsoft® Transaction Integrator Concurrent Server|  
|0x02|Info|User Data|  
|0x07|Info|Execution OK|  
  
## Error codes  
 The following table shows the meaning of the error codes.  
  
|Code|Type|Meaning|  
|----------|----------|-------------|  
|0x03|Error|Invalid ProgID|  
|0x04|Error|Invalid TranID|  
|0x05|Error|Inquiry Failed|  
|0x06|Error|Inquiry Status|  
|0x08|Error|Program ABEND|  
|0x09|Error|Execution Failed|  
|0x0A|Error|Invalid ELM|  
  
 For more information about the format of the TRM, see the TRM definition file at \<drive>:\Program Files\ Microsoft Host Integration Server\System\TIM\MicrosoftTRMDefs.tim. Use Visual Studio to view the file.  
  
## See Also  
 [ELM Format for the TCP ELM User Data Programming Model](../core/elm-format-for-the-tcp-elm-user-data-programming-model2.md)   
 [Enhanced Listener CICS Administration](../core/enhanced-listener-cics-administration2.md)