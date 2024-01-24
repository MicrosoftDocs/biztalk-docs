---
description: "Learn more about: SDLC Outage Codes"
title: "SDLC Outage Codes2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SDLC Outage Codes
The following table describes Synchronous Data Link Control (SDLC) outage codes.  
  
|Outage code|Description|  
|-----------------|-----------------|  
|0x0D|Internally generated for SNALink lost locality.|  
|0x11|Data set ready (DSR) failure.|  
|0x12|Clear to send (CTS) failure.|  
|0x14|Data carrier detect (DCD) failure.|  
|0x24|Nonproductive receive retry limit exceeded.|  
|0x25|Idle time-out retry limit exceeded.|  
|0x29|Connection problem. subqual = 0x00I-frame retransmission subqual nonzeroXID retransmission|  
|0x2D|Abnormal modem response.|  
|0x2E|Write time-out retry exceeded.|  
|0xA0|Exchange identification (XID) exchange failed on multidrop line. Subqual is address of secondary station.|  
|0x15|Discontact (DISC) received.|  
|0x23|Receive buffer overrun.|  
|0x2C|Invalid command received. subqual = 0x03invalid N(R) subqual = 0x04invalid or unsupported command/response subqual = 0x05excess I-field|  
|0x80|Disconnect mode (DM) received in information transfer state.|  
|0x81|Discontact retry limit exceeded.|  
|0x82|Contact retry limit exceeded.|  
|0x83|Poll retry limit exceeded.|  
|0x84|No response retry limit exceeded.|  
|0x85|Remote busy retry limit exceeded.|  
|0x86|Frame reject (FRMR) received. subqual = 0x00no reason given subqual = 0x03invalid N(R) subqual = 0x04invalid or unsupported command/response subqual = 0x05excess I-field|  
|0x87|Invalid frame received. subqual = 0x03invalid N(R) invalid or unsupported command/response subqual = 0x05excess I-field|  
|0x88|Request Initialization Mode (RIM) received.|  
|0x89|Request Disconnect (RD) received.|
