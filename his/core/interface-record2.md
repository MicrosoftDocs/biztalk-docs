---
description: "Learn more about: Interface Record"
title: "Interface Record2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Interface Record
Status information is transferred between the driver and the SNALink using a buffer known as the interface record.  
  
 The driver allocates this buffer when it starts and maintains the information in it while it is running. The contents of this buffer are copied to an SNALink buffer by using an IOCTL call of type **READ_INTERFACE_RECORD**.
