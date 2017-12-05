---
title: "Interface Record1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a72e123-41fb-40e8-a07f-7d5eda57c97d
caps.latest.revision: 3
---
# Interface Record
Status information is transferred between the driver and the SNALink using a buffer known as the interface record.  
  
 The driver allocates this buffer when it starts and maintains the information in it while it is running. The contents of this buffer are copied to an SNALink buffer by using an IOCTL call of type **READ_INTERFACE_RECORD**.