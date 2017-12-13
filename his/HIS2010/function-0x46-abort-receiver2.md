---
title: "Function 0x46: Abort Receiver2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b29f69f0-d68b-4a99-9856-61e8475ac834
caps.latest.revision: 3
---
# Function 0x46: Abort Receiver
The SNALink calls this function to clear down the driver's receiver.  
  
## Remarks  
 This request causes the driver to stop the receiver and to flush its internal buffers of any received data. It should be used to clear down the receiver, for instance, before altering the link characteristics.