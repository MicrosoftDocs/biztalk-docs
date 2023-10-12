---
description: "Learn more about: Sending Binary Data to the Host"
title: "Sending Binary Data to the Host2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Sending Binary Data to the Host
The Transaction Integrator (TI) run-time environment does not translate binary data (Byte in Visual Basic, VT_UI1 in Automation, or unsigned char in C++) when it sends it to the mainframe. Instead, TI copies the binary data unchanged into a PIC X data representation on the mainframe. To define a string of binary data, define it as an array.  
  
## See Also  
 [Host and Automation Data](../core/host-and-automation-data1.md)
