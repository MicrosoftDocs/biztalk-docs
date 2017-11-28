---
title: "Configuration Parameters for Send and Receive Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters"
  - "send adapters"
  - "configuration parameters [adapters]"
  - "receive adapters"
ms.assetid: f24ca8ae-feaf-4e5f-b434-76bc3c1c8ccf
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuration Parameters for Send and Receive Adapters
This section provides configuration parameters for send and receive Minimal Lower Layer Protocol (MLLP) adapters. These parameters fall into two types: block characters and network connection parameters.  
  
 You set the block character settings in the MLLP Transport Properties for a send port using the MLLP transport type.  
  
 You can set the network connection parameters in the MLLP Transport Properties for either a send port or receive location using the MLLP transport type. To do so, open the BizTalk Server Administration Console, navigate either to the Send Ports or Receive Locations folder, as applicable, right-click the specific send port or receive location, click **Properties**, and then click **Configure**.  
  
## Block Characters  
 These parameters are special characters that must enclose HL7 messages received or sent through MLLP adapters. These characters form a block in the following format: \<SB\>*DDD*\<EB\>\<CR\>, where *DDD* stands for the message data, \<SB\> is the start-block character, \<EB\> is the end-block character, and \<CR\> is the carriage return.  
  
|Parameter|Use|  
|---------------|---------|  
|**\<CR\> Carriage Return**|Byte value (in hexadecimal format) that you use for the carriage return (the second byte wrapper after the end byte). Optional.|  
|**\<EB\> End-Block character**|Byte value that you use for the end byte (message trailer wrapper). ASCII \<FS\>, for example, \<1c\>.|  
|**\<SB\> Start-Block character**|Byte value that you use for the start byte (message header wrapper). ASCII \<VT\>, for example, \<0b\>.|  
  
## DeliveryMode  
 You use the delivery mode parameter to control whether instance files are delivered in sequence, or out of sequence (in order, out of order). Each receive location has its own delivery sequence for instance files.  
  
|Use this|To do this|  
|--------------|----------------|  
|Ordered Delivery|**MLLP Receive**:<br /><br /> Set the **Ordered Delivery** property to **TRUE**, to specify that messages should be processed in a specified order. Ordered delivery is important for messages that must be processed as a convoy, as specified by a partner business process.<br /><br /> If you set the **Ordered Delivery** property to **FALSE** (the default value), the port does not enforce ordered delivery.|  
  
## Network Connection Parameters  
 You use these parameters to establish a connection over the network, including comments, connection name, host name, port ID, receive timeout, and send timeout.  
  
|Parameter|Use|  
|---------------|---------|  
|**Comments**|Description of connection. Optional.|  
|**Connection Name**|Name of monitored connection. It is recommended that the name be unique. The name is included in the name of performance counter instances for this connection.|  
|**Host**|**MLLP Receive**:<br /><br /> Optional. Specify a local interface on which to listen for incoming connections. By default listens on all local interfaces.<br /><br /> **MLLP Send**:<br /><br /> Specify the NetBIOS name or IP address of the line-of-business (LOB) computer to which you want to connect.|  
|**Persistent Connection**|**MLLP Receive**:<br /><br /> Set the **Persistent Connection** property to **FALSE** (the default value), to close the connection after the connection is idle for the timeout period. Set the **Persistent Connection** property to **True**, to keep the connection open.<br /><br /> The following table shows the results for the possible values of the **Persistent Connection** and **Receive Timeout** values.<br /><br /> **FALSE**<br /><br /> - >0<br /><br /> - The connection closes after a message is received or the timeout period elapses.<br /><br /> **FALSE**<br /><br /> - 0<br /><br /> - Causes an error condition: "Receive Timeout value should not be zero in case of persistent connection FALSE."<br /><br /> **TRUE**<br /><br /> - 0<br /><br /> - The connection never breaks.<br /><br /> **TRUE**<br /><br /> - <>0<br /><br /> - Causes an error condition: "Receive Timeout value should be zero in case of persistent connection TRUE."<br /><br /> **MLLP Send**:<br /><br /> Set the **Persistent Connection** property to **FALSE**, to close the connection if a response is received within the timeout period, or if the timeout period elapses. Set the **Persistent Connection** property to **True** (the default value), to keep the connection open.<br /><br /> The following table shows the results for the possible values of the **Persistent Connection** and **Receive Timeout** values.<br /><br /> **FALSE**<br /><br /> - O or >0<br /><br /> - The connection closes after a response is received or the timeout period elapses.<br /><br /> **TRUE**<br /><br /> - 0 or <>0<br /><br /> - The connection never breaks. The **Send Timeout** value does not impact the status of the connection.<br /><br /> The following table shows the connection status for different send port types when the settings for persistent connection and solicit response are changed.<br /><br /> Static one-way<br /><br /> - TRUE<br /><br /> - No<br /><br /> - Remains open<br /><br /> Static one-way<br /><br /> - TRUE<br /><br /> - Yes<br /><br /> - Remains open<br /><br /> Static one-way<br /><br /> - FALSE<br /><br /> - No<br /><br /> - Closed<br /><br /> Static one-way<br /><br /> - FALSE<br /><br /> - Yes<br /><br /> - Closed<br /><br /> Static solicit response<br /><br /> - TRUE<br /><br /> - No<br /><br /> - Remains open<br /><br /> Static solicit response<br /><br /> - TRUE<br /><br /> - Yes<br /><br /> - Remains open<br /><br /> Static solicit response<br /><br /> - FALSE<br /><br /> - No<br /><br /> - Closed<br /><br /> Static solicit response<br /><br /> - FALSE<br /><br /> - Yes<br /><br /> - Closed|  
|**Port**|**MLLP Receive**:<br /><br /> Local port ID to listen on.<br /><br /> **MLLP Send**:<br /><br /> Remote port ID to which you want to connect.|  
|**Send Timeout**|**MLLP Send**:<br /><br /> The maximum time the send adapter will wait while sending a message, after which the sending socket will time out. Upon expiration, BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) will retry the message.<br /><br /> Also, in case of synchronous operation of the send port, the maximum time for receiving the acknowledgment (ACK) from the LOB.|  
|**Receive Timeout**|**MLLP Receive**:<br /><br /> The maximum time that the receive adapter will wait while receiving a message, after which the receiving socket will time out. Upon expiration, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will close the connection.<br /><br /> Also, in case of synchronous operation of the receive location, the maximum time for sending the ACK to the LOB.|  
|**Solicit Response Enabled**|**MLLP Send**:<br /><br /> Yes/No. Enables receiving ACKs on the same TCP connection.|  
|**Submit Receive Location URI for ACK**|**MLLP Send**:<br /><br /> URI of the receive location under which the ACKs received on the same TCP connection will be delivered to the MessageBox database.|  
  
## See Also  
 [Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [MLLP Receive Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [MLLP Send Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)