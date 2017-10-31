---
title: "Function 0x64: Read Interface Record2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69a6d971-f877-44b7-82d5-4539e6d352c4
caps.latest.revision: 3
---
# Function 0x64: Read Interface Record
This function reads the driver's interface record and copies it into the buffer passed by the SNALink. The buffer must be allocated by the SNALink prior to making this call.  
  
## Parameters  
 **IRP.System.Buffer**  
 Interface Record Address (IN)—a 32-bit pointer to the driver's interface record area.  
  
 The interface record format is as follows:  
  
|Description|Type|  
|-----------------|----------|  
|Received Frames|**int**|  
|Transmit Buffer Space|**int**|  
|Status Events|**int**|  
|Input V.24 Status|**UCHAR**|  
|Output V.24 Status|**UCHAR**|  
|Statistics Counters|**int[11]**|  
  
-   Received Frames is the number of frames currently queued in the driver receive buffers.  
  
-   Transmit Buffer Space is used to signal to the SNALink:  
  
     Whether more frames can be provided to the driver.  
  
     Whether the driver still has frames waiting to be sent.  
  
     The Transmit Buffer Space field indicates the maximum frame size that the driver can currently accept. This is updated after each successful Transmit Frame IOCTL, and should be checked by the SNALink before sending further frames to the driver.  
  
-   Status Events is a count of the total number of increments made to the Statistics Counters.  
  
-   Input V.24 Status is a bitmap of the current logical state of the input interface lines, a value of 1 meaning ON and a value of 0 meaning OFF. The pins are mapped as follows:  
  
    |Bit number|V.24 circuit name|Circuit number|RS-232C pin|  
    |----------------|-----------------------|--------------------|------------------|  
    |7 - 5|Reserved|142|25|  
    |4|Test Indicator|125|22|  
    |3|Calling Indicator|125|22|  
    |2|RLSD (commonly DCD)|109|8|  
    |1|Data Set Ready (DSR)|107|6|  
    |0|Clear to send (CTS)|106|5|  
  
-   Output V.24 Status is a bitmap of the current logical state of the output interface lines, a value of 1 meaning ON and a value of 0 meaning OFF. The pins are mapped as follows:  
  
    |Bit number|V.24 circuit name|Circuit number|RS-232C pin|  
    |----------------|-----------------------|--------------------|------------------|  
    |7 - 5|Reserved|||  
    |4|Maintenance Test|140|18|  
    |3|Select Standby|116|11|  
    |2|Data Signal Rate Selector|111|23|  
    |1|Data Terminal Ready (DTR)|108/2|22|  
    |0|Request to Send (RTS)|105|4|  
  
     Note that the driver will raise and lower RTS as necessary while transmitting, reflecting the state of RTS in the output V.24 status field. The application should not, therefore, try to manipulate RTS.  
  
-   The Statistics Counters are running counts of various kinds of link status information.The events they relate to are:  
  
    |Counter number|Description|  
    |--------------------|-----------------|  
    |1|Frames received with incorrect CRC.|  
    |2|Frames larger than the maximum size received.|  
    |3|Frames smaller than 32 bits received.|  
    |4|Frames received that are not a multiple of 8 bits.|  
    |5|Aborted frames received.|  
    |6|Transmitter underruns.|  
    |7|Receiver overruns.|  
    |8|RLSD drops in mid-reception.|  
    |9|CTS drops in mid-transmission.|  
    |10|DSR drops.|  
    |11|Hardware failures (adapter or modem).|  
  
## Remarks  
 The interface record provides a fast mechanism to use to decide whether a frame can be transmitted, whether there are any frames to be received, and so on. The driver maintains this information. Each time the SNALink requires this information, it calls **Read Interface Record** to get a copy of the current interface record. After each call, the driver clears the statistics counters in its own interface record. The V.24 status and transmit and receive data information are unchanged.