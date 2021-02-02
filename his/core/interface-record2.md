---
description: "Learn more about: Interface Record"
title: "Interface Record2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f123abd-5af4-43a1-b136-826a7314f8b8
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Interface Record
Status information is transferred between the driver and the SNALink using a buffer known as the interface record.  
  
 The driver allocates this buffer when it starts and maintains the information in it while it is running. The contents of this buffer are copied to an SNALink buffer by using an IOCTL call of type **READ_INTERFACE_RECORD**.
