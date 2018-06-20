---
title: "OPEN Call2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0572d64d-9583-43d1-b6a0-b7a3858569ab
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# OPEN Call
The **OPEN** call has no parameters. It grants access to the driver from a particular process. The driver ensures that only one **OPEN** is accepted by the link at any one time. When **OPEN** is processed, the driver attempts to reserve access to hardware resources such as interrupt vectors. The **OPEN** is rejected if this fails.  
  
 After a successful **OPEN** request, the driver expects to receive the following IOCTL commands:  
  
- **SET_EVENT_HANDLE**  
  
- **SET_INTERFACE_RECORD**  
  
- **SET_LINK_CHARACTERISTICS**  
  
  Of these, the first two can be performed in any order, but both should be issued before calling **SET_LINK_CHARACTERISTICS**.  
  
  When these three calls have been successfully performed by the SNALink, the driver is ready for information transfer.