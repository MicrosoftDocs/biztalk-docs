---
title: "Expanded Information About Message Formats for Open(LINK) Request with SDLC1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca0e0307-f3a0-472d-86e4-dbe37fae9c46
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Expanded Information About Message Formats for Open(LINK) Request with SDLC
The following list supplements the information found in the table in [Open(LINK) Request](../core/open-link-request1.md). The timers described in the lists are used by a synchronous data link control (SDLC) link service to determine when to retry communication and when to generate outages. Generally, after the time interval specified by the time-out (usually 1000 milliseconds), the communication is retried. The cycle of time-out and retry is repeated until the retry limit is reached. Then an [Outage](../core/outage2.md) message is sent by the SDLC link service.  

 With some timers, there are no communication retries. Such timers simply cycle through the time-out as many times as allowed in the retry limit (without actually retrying), then generate an **Outage** message.  

 Each description indicates whether you can configure the field through a Microsoft Host Integration Server interface (such as the SNA Manager program). If the field is not configurable, the built-in setting for the field is shown.  

## SDLC Link Data  

-   *dataru[s+22] XID supplied*  

     This field controls whether an initial exchange identification (XID) is sent on this connection. The value used is determined by the leased or switched setting for the line:  

     Leased line: 0x00  Do not send an initial XID. Switched line: 0x01  Send an initial XID (may be a NULL XID).  

     A line is configured as leased or switched in Host Integration Server Setup.  

-   *dataru[s+24] Use Reject_Command indicator*  

     This field determines that the link service will not send a Reject command (an SDLC command, not often used, value 0x19) if a frame is received with an invalid next-to-send (NS) value. Instead, the link service waits until the next poll before requesting retransmission of the frame.  

     This field is not configurable and must remain at the setting of "Do not use."  

-   *Station Timers (described for SDLC only)*  

-   dataru[s+28..s+29] Contact time-out  

-   dataru[s+30..s+31] Contact retry limit  

     This timer is started when an XID or set normal response mode (SNRM) is transmitted. If the time-out expires without acknowledgment, the frame is retransmitted. When the number of retransmitted frames reaches the retry limit, an outage is generated. Note that for XIDs, the time-out value is randomized to prevent possible clashes between two servers sending XIDs simultaneously.  

     This timer is configurable in SNA Manager, in the advanced settings for an SDLC connection.  

-   *dataru[s+32..s+33] Discontact time-out*  

-   *dataru[s+34..s+35] Discontact retry limit*  

     This timer is started when a discontact (DISC) is sent. It is stopped when an unnumbered acknowledgment (UA) or disconnect mode (DM) is received. If the number of sent DISCs reaches the retry limit, an outage is generated.  

     This timer is not configurable. The discontact time-out is 1000 milliseconds; the discontact retry limit is 3.  

-   *dataru[s+36..s+37] Negative poll time-out*  

-   *dataru[s+38..s+39] Negative poll retry limit*  

     This timer is used for primary SDLC only. At intervals specified by the negative poll time-out, a receive ready (RR) is transmitted. The negative poll retry limit is set at no limit; therefore, no outage is generated, no matter how many RRs are transmitted without acknowledgment being received.  

     The negative poll time-out is configurable in SNA Manager, in the advanced settings for an SDLC connection, where the time-out is called poll rate. Poll rate is set in polls per second (and translated internally into the negative poll time-out, timed in milliseconds).  

     The negative poll retry limit is not configurable. It is set at –1, meaning no limit.  

-   *dataru[s+40..s+41] T1 (no acknowledgment) time-out*  

-   *dataru[s+42..s+43] N2 (no acknowledgment) retry limit*  

     This timer is used for primary SDLC and is started when a poll/final bit is expected. If the time-out expires before a frame containing a poll/final bit is received, an RR is sent. When the number of sent RRs reaches the retry limit, an outage is generated.  

     This timer is configurable in SNA Manager, in the advanced settings for an SDLC connection, where it is called the poll time-out and poll retry limit.  

-   *dataru[s+44..s+45] Remote station busy time-out*  

-   *dataru[s+46..s+47] Remote station busy retry limit*  

     This timer is used for primary SDLC and is started when a receive not ready (RNR) is received. It is stopped when an RR is received. If the time-out expires the number of times specified by the retry limit, an outage is generated.  

     This timer is not configurable. The remote station busy time-out is 1000 milliseconds. The remote station busy retry limit is 30. Therefore, the time allowed before an outage is 30 seconds.  

## Link Timers (described for SDLC only)  

- *dataru[s+48..s+49] Idle time-out*  

- *dataru[s+50..s+51] Idle retry limit*  

   This timer is configurable in SNA Manager, in the advanced settings for an SDLC connection.  

- *dataru[s+52..s+53] Nonproductive receive time-out*  

- *dataru[s+54..s+55] Nonproductive receive retry limit*  

   This timer is used for secondary SDLC only and is started when any frame is received for this station. It is stopped when additional frames are received for this station. If the time-out expires the number of times specified by the retry limit, the link service causes a pop-up message, but does not generate an outage (because multidrop lines can be very slow).  

   This timer is not configurable. The nonproductive receive time-out is 1000 milliseconds (1 second); the nonproductive receive retry limit is 60. Therefore, the time allowed before a pop-up message is 60 seconds.  

- *dataru[s+56..s+57] Write time-out*  

- *dataru[s+58..s+59] Write retry limit*  

   This timer is started after an information frame has been transmitted to the hardware and stopped when the hardware acknowledges the frame. If the time-out expires the number of times specified by the retry limit, an outage is generated.  

   This timer is not configurable. The write time-out is 1000 milliseconds (one second). The write retry limit is 15. Therefore, the time allowed before an outage is 15 seconds.  

- *dataru[s+60..s+61] Link connection time-out*  

- *dataru[s+62..s+63] Link connection retry limit*  

   This timer is started when an open link for a leased line is received, and stopped when Data Set Ready (DSR) is raised. If the time-out expires the number of times specified by the retry limit, an outage is generated.  

   This timer is not configurable. The link connection time-out is 1000 milliseconds (one second). The link connection retry limit is 300. Therefore, the time allowed before an outage is 300 seconds.  

  |X.25 link data|Description|  
  |--------------------|-----------------|  
  |dataru[s+22]|Circuit type 0x00 PVC 0x01 SVC|  
  |dataru[s+23]|PVC alias, starting at 1 for lowest PVC channel number (reserved for SVC).|  
  |dataru[s+24..s+25]|PVC packet size (reserved for SVC).|  
  |dataru[s+26]|Default level 3 window size for PVC (reserved for SVC).|  
  |dataru[s+27]|Link role: 0x00 Primary 0x01 Secondary 0x02 Negotiable|  

  |802.2 link data|Description|  
  |---------------------|-----------------|  
  |dataru[s+22]|Maximum receives without a transmit acknowledgment.|  
  |dataru[s+23]|Maximum transmits without a receive acknowledgment.|  
  |dataru[s+24]|Dynamic window increment value.|  
  |dataru[s+25]|Remote local service access point (SAP) address.|  
  |dataru[s+26]|Local SAP address (for incoming calls).|  
  |dataru[s+27]|Value for t1 timer multiplier.|  
  |dataru[s+31]|Value for t2 timer multiplier.|  
  |dataru[s+35]|Value for t3 timer multiplier.|  
  |dataru[s+42]|Maximum retry count (N2 value). Note that this 802.2 link data is required for the 802.2 command DLC.OPEN.STATION.|  

   Note that if the fields in the preceding table for timer multipliers are set to zero, the SNALink should use appropriate defaults.  

  |End of link data section|Description|  
  |------------------------------|-----------------|  
  |dataru[s+68..s+69]|Length of link connection data (= a) (0x0000) None present|  
  |dataru[s+70..s+70+a]|Link connection data|  
  |dataru[s+70+b..s+71+b]|Where b is maximum of a and 20. Size of XID I-frame (= n) (0x0000) NULL XID|  
  |dataru[s+72+b]|XID|  

   Note that if there are 20 or fewer bytes of link connection data, the XID length is at s+90 and the actual XID starts at s+92.  

  The link connection data can contain one of the following:  

- Media access control (MAC) address of remote station  

- X.25 address of remote station  

- Dial-digits for manual or auto-dial modems
