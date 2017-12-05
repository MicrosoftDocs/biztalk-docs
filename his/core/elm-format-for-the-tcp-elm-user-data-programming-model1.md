---
title: "ELM Format for the TCP ELM User Data Programming Model1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff6f70b7-b5b5-4884-a8b3-8ae3bc02df67
caps.latest.revision: 4
---
# ELM Format for the TCP ELM User Data Programming Model
This section describes the format and content of the enhanced listener message (ELM) used by the TCP ELM User Data programming model.  
  
## ELM Request Message  
 The following table shows the contents of the request message.  
  
|Client in data|  
|--------------------|  
|35|  
  
 Client in data  
 35 bytes of data used by the CICS TCP/IP security exit and passed to the Concurrent Server in the transaction initiation message (TIM).  
  
## Client in data for Microsoft Security Exit format  
 The following code block describes the format of the client in data for the Microsoft security exit.  
  
## Syntax  
  
```  
struct CLIENT_IN_DATA {  
   BYTE    bUserID[8];  
   BYTE    bPassword[8];  
   BYTE    bReserved[19];  
} UNALIGNED;  
```  
  
## Client in data for IBM Security Exit format  
 The following code block describes the format of the client in data for the IBM security exit.  
  
## Syntax  
  
```  
struct CLIENT_IN_DATA2 {  
   BYTE    bSecFlag;  
   BYTE    bPassword[8];  
   BYTE    bUserID[8];  
   BYTE    bReserved[18];  
} UNALIGNED;  
```  
  
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
|0x01|Info|Version ID for Microsoft Transaction Integrator Concurrent Server|  
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
 [ELM Format for the TCP ELM Link Programming Model](../core/elm-format-for-the-tcp-elm-link-programming-model2.md)   
 [Enhanced Listener CICS Administration](../core/enhanced-listener-cics-administration1.md)