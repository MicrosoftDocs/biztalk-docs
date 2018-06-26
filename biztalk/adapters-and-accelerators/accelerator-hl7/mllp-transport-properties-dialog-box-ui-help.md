---
title: "MLLP Transport Properties Dialog Box UI Help | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "btahl7.mllp.transportproperties"
ms.assetid: 2a41aaeb-a91d-4d89-ac8a-1cfe48ab4cd4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MLLP Transport Properties Dialog Box UI Help
You use the **MLLP Transport Properties** dialog box to configure parameters for send and receive Minimal Lower Layer Protocol (MLLP) adapters. You can set the network connection parameters in the MLLP Transport Properties for either a send port or receive location using the MLLP transport type.  

 For more information about MLLP properties, see [Configuration Parameters for Send and Receive Adapters](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md).  

## UIElement List  
 In the **MLLP Transport Properties** dialog box, do the following:  

#### Block Characters  
 Block character parameters are special characters that must enclose HL7 messages received or sent through MLLP adapters. These characters form a block in the following format: \<SB\>*DDD*\<EB\>\<CR\>, where *DDD* stands for the message data, \<SB\> is the start-block character, \<EB\> is the end-block character, and \<CR\> is the carriage return.  

|Use this|To do this|  
|--------------|----------------|  
|**\<CR\> Carriage Return**|Byte value (in hexadecimal format) that you use for the carriage return (the second byte wrapper after the end byte). Optional.|  
|**\<EB\> End-Block character**|Byte value that you use for the end byte (message trailer wrapper). ASCII \<FS\>, for example, \<1c\>.|  
|**\<SB\> Start-Block character**|Byte value that you use for the start byte (message header wrapper). ASCII \<VT\>, for example, \<0b\>.|  

#### DeliveryMode  
 You use the delivery mode parameter to control whether instance files are delivered in sequence, or out of sequence (in order, out of order). Each receive location has its own delivery sequence for instance files.  

|Use this|To do this|  
|--------------|----------------|  
|Ordered Delivery|**MLLP Receive**:<br /><br /> If you set the **Ordered Delivery** property to **FALSE** (the default value), the instance files will not be delivered in sequence. Smaller instance files pushed in to the queue after larger instance files, will be delivered first. Set the **Ordered Delivery** property to **TRUE**, to deliver instance files in sequence.|  

#### Network Connection Parameters  
 You use network connection parameters to establish a connection over the network, including comments, connection name, host name, port ID, receive timeout, and send timeout.  


|                Use this                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          To do this                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              **Comments**               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Description of connection. Optional.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|           **Connection Name**           |                                                                                                                                                                                                                                                                                                                                                                                                                Name of monitored connection. It is recommended that the name be unique. The name is included in the name of performance counter instances for this connection.                                                                                                                                                                                                                                                                                                                                                                                                                |
|                **Host**                 |                                                                                                                                                                                                                                                                                                                                         **MLLP Receive**:<br /><br /> Optional. Specify a local interface on which to listen for incoming connections. By default listens on all local interfaces.<br /><br /> **MLLP Send**:<br /><br /> Specify the NetBIOS name or IP address of the line-of-business (LOB) computer to which you want to connect.                                                                                                                                                                                                                                                                                                                                         |
|        **Persistent Connection**        | **MLLP Receive**:<br /><br /> Set the **Persistent Connection** property to **FALSE** (the default value), to close the connection after the connection is idle for the timeout period. Set the **Persistent Connection** property to **True**, to keep the connection open.<br /><br /> **MLLP Send**:<br /><br /> Set the **Persistent Connection** property to **FALSE**, to close the connection if a response is received within the timeout period, or if the timeout period elapses. Set the **Persistent Connection** property to **True** (the default value), to keep the connection open.<br /><br /> See [Persistent Connection and Receive Timeout Values](../../adapters-and-accelerators/accelerator-hl7/mllp-transport-properties-dialog-box-ui-help.md#persistentConnectionAndReceiveTimeout), and [Port Types and Connection Status](../../adapters-and-accelerators/accelerator-hl7/mllp-transport-properties-dialog-box-ui-help.md#portTypeConnectionStatus) for details. |
|                **Port**                 |                                                                                                                                                                                                                                                                                                                                                                                                                         **MLLP Receive**:<br /><br /> Local port ID to listen on.<br /><br /> **MLLP Send**:<br /><br /> Remote port ID to which you want to connect.                                                                                                                                                                                                                                                                                                                                                                                                                         |
|            **Send Timeout**             |                                                                                                                                                                                                                                                                    **MLLP Send**:<br /><br /> The maximum time the send adapter will wait while sending a message, after which the sending socket will time out. Upon expiration, BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) will retry the message.<br /><br /> Also, in case of synchronous operation of the send port, the maximum time for receiving the acknowledgment (ACK) from the LOB.                                                                                                                                                                                                                                                                    |
|           **Receive Timeout**           |                                                                                                                                                                                                                                                                                 **MLLP Receive**:<br /><br /> The maximum time that the receive adapter will wait while receiving a message, after which the receiving socket will time out. Upon expiration, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will close the connection.<br /><br /> Also, in case of synchronous operation of the receive location, the maximum time for sending the ACK to the LOB.                                                                                                                                                                                                                                                                                 |
|      **Solicit Response Enabled**       |                                                                                                                                                                                                                                                                                                                                                                                                                                                     **MLLP Send**:<br /><br /> Yes/No. Enables receiving ACKs on the same TCP connection.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **Submit Receive Location URI for ACK** |                                                                                                                                                                                                                                                                                                                                                                                                                 **MLLP Send**:<br /><br /> URI of the receive location under which the ACKs received on the same TCP connection will be delivered to the MessageBox database.                                                                                                                                                                                                                                                                                                                                                                                                                 |

#####  <a name="persistentConnectionAndReceiveTimeout"></a> Persistent Connection and Receive Timeout Values  
 For **MLLP Receive**, the following table shows the results for the possible values of the **Persistent Connection** and **Receive Timeout** values.  

|**Persistent Connection**|**Receive Timeout**|Result|  
|-------------------------------|-------------------------|------------|  
|**FALSE**|>0|The connection closes after a message is received or the timeout period elapses.|  
|**FALSE**|0|Causes an error condition: "Receive Timeout value should not be zero in case of persistent connection FALSE."|  
|**TRUE**|0|The connection never breaks.|  
|**TRUE**|<>0|Causes an error condition: "Receive Timeout value should be zero in case of persistent connection TRUE."|  

 For **MLLP Send**, the following table shows the results for the possible values of the **Persistent Connection** and **Receive Timeout** values.  

|**Persistent Connection**|**Send Timeout**|Result|  
|-------------------------------|----------------------|------------|  
|**FALSE**|0 or >0|The connection closes after a response is received or the timeout period elapses.|  
|**TRUE**|0 or <>0|The connection never breaks. The **Send Timeout** value does not impact the status of the connection.|  

#####  <a name="portTypeConnectionStatus"></a> Port Types and Connection Status  
 The following table shows the connection status for different send port types when the settings for persistent connection and solicit response are changed.  

|Send port type|Persistent connection|Solicit response|Connection status|  
|--------------------|---------------------------|----------------------|-----------------------|  
|Static one-way|TRUE|No|Remains open|  
|Static one-way|TRUE|Yes|Remains open|  
|Static one-way|FALSE|No|Closed|  
|Static one-way|FALSE|Yes|Closed|  
|Static solicit response|FALSE|Yes|Remains open|  
|Static solicit response|TRUE|Yes|Remains open|  
|Static solicit response|FALSE|No|Closed|  
|Static solicit response|FALSE|Yes|Closed|  

## See Also  
 [Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [MLLP Receive Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [MLLP Send Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)