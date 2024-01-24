---
description: "Learn more about: Supporting Modem Status in an SNA Link Service"
title: "Supporting Modem Status in an SNA Link Service1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Supporting Modem Status in an SNA Link Service
The implementation of a link service that supports the modem status requires the following:  
  
- A call to the SNA Modem interface to initialize the SNA Modem data structures.  
  
- Modification of the SNA Modem structures as the status changes, as reported by the **DevIoctl** calls.  
  
  Independent hardware vendors (IHVs) who use the MicrosoftHost Integration Server SDLC link service and who fully implement the SNADIS interface do not need to make any changes to use the modem status feature. However, IHVs should check that the status returned by **DevIoctl** calls from their device driver conforms to the requirements described later.  
  
  IHVs who provide both the device driver and link service need to implement the code in their link service that initializes the SNA Modem API and updates the modem status information.
