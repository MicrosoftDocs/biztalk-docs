---
title: "TRM Format for the TCP TRM Link Programming Model1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 768d6eaa-1dca-417b-a7de-f77f40da0e28
caps.latest.revision: 4
---
# TRM Format for the TCP TRM Link Programming Model
This topic describes the format and content of the transaction request message (TRM) used by the TCP TRM Link programming model.  
  
## TRM Request Message  
 The following table shows the contents of the request message.  
  
|TranID|Comma|Client in data|  
|------------|-----------|--------------------|  
|4|1|35|  
  
 TranID  
 Transaction ID of the Concurrent Server to be started by the Listener.  
  
 Comma  
 A comma (,) separates the transaction ID from the Client in data.  
  
 Client in data  
 35 bytes of data used by the CICS TCP/IP security exit and passed to the Concurrent Server in the transaction initiation message (TIM).  
  
## Client in data for Microsoft Security Exit format  
 The following code block describes the format of the client in data for the Microsoft security exit.  
  
## Syntax  
  
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
  
## Syntax  
  
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
  
## TRM Reply Message  
 The following table shows the contents of the reply message.  
  
|TRM reply msg length|Formatted field length|Formatted field code|*Data*|  
|--------------------------|----------------------------|--------------------------|------------|  
|4|4|1|*0-n*|  
  
> [!NOTE]
>  The formatted field length, formatted field code, and data can be repeated multiple times in a single message.  
  
 TRM reply msg length  
 The total length of the TRM reply message. This length is the sum of all the lengths of the formatted fields that follow in the message and does not include the length of the TRM reply msg length field itself.  
  
 Formatted field length  
 The length of the formatted field.  
  
 The formatted field length is the sum of the combination of the Formatted field code length and the Data length.  
  
 Formatted field code  
 A 1-byte code that describes the information passed from the Concurrent Server back to the client.  
  
 You cannot change the Formatted field code.  
  
 The field codes are specific to the communication handling between the WIP and HIP TCP Transports and the MSCMTICS, MSHIPLNK and TCP Concurrent Server programs.  
  
 *Data*  
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
|0x0A|Error|Invalid TRM|  
  
 For more information about the format of the TRM, see the TRM definition file at \<drive>:\Program Files\Microsoft Host Integration Server\System\TIM\MicrosoftTRMDefs.tim. Use Visual Studio to view the file.  
  
## See Also  
 [TRM Format for the TCP TRM User Data Programming Model](../core/trm-format-for-the-tcp-trm-user-data-programming-model1.md)