---
description: "Learn more about: Error Codes for Open(SSCP) Error Response"
title: "Error Codes for Open(SSCP) Error Response2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Error Codes for Open(SSCP) Error Response
The following table gives the values for error code 1 and error code 2 that can be returned on the **Open(SSCP) Error Response**.  
  
|Error code 1|Description|Error code 2|Description|  
|------------------|-----------------|------------------|-----------------|  
|0|No servers found.|CSRENOSR (0)|No servers found.|  
|0x0053|Logical unit (LU) not verified.|CSRECBSH (3)|LU not verified.|  
|0x0055|System services control point (SSCP) connection already open.|CSRECBSH (3)|Control block / resource shortage.|  
|0x0057|No LU in group free.|||  
|0x0812|No free session control block available.|||  
|0x1001|A connection activation failed recently.|||  
|0x1002|The connection is inactive.|||  
|0x1008|The link service is active remotely. This error return code is not supported by this level of Host Integration Server.|||  
|0x1009|The SNA server is active, but the connection on which the requested LU is defined is not active.|||  
|0x100B|The connection is in the process of activating as the result of another **Open(SSCP)** or operator activation or recovery from an outage.|||  
|0x1010|The connection is active, but an activate physical unit (ACTPU) has not yet been received.|||  
|0x1011|The connection is active, but an activate logical unit (ACTLU) has not yet been received.|||  
|0x0063|Unrecognized Open request.|CSRESERV (1)|Service not present.|  
|0x0A0E|LU/LU group not found in configuration.|||  
  
> [!NOTE]
>  The error code 1 values 0x1001 to 0x1011 are returned when the [Open(SSCP) Request](./open-sscp-request2.md) specifies a nonforced Open. They do not indicate errors, but indicate that the LU-SSCP session is not active. The application can retry the **Open(SSCP) Request** specifying a forced Open, in which case the local node will attempt to activate the connection if possible.
