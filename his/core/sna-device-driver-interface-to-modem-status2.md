---
title: "SNA Device Driver Interface to Modem Status2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 075bfac0-51be-4818-82bb-ed78248dfa00
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# SNA Device Driver Interface to Modem Status
There are three interfaces from which modem status can be gathered:  
  
- The SNADIS Dumb Card Interface **GetV24Status** IOCTL call that reports the status of the Ring Indicator (DRI), Carrier Detect (DCD), Clear To Send (CTS), and Data Set Ready (DSR) signal lines.  
  
- The SNADIS Dumb Card Interface **SetV24Status** IOCTL call that sets the status of the Data Terminal Ready (DTR) and Request To Send (RTS) signal lines.  
  
- The SNADIS Dumb Card Interface receive and transmit IOCTL calls, used to set the operating mode of the device driver.  
  
  Whenever one of the first two interfaces indicates a modem line is high, the corresponding light in the display is lit. However, the transmit and receive IOCTL calls cannot provide a definitive statement as to whether the card is receiving data, only that it is ready to receive data. To work around this limitation and to have the modem lights give a reasonable indication of ordinary data throughput, the following mechanism is recommended:  
  
  Simulate the receive and transmit lights with counters and track the number of frames received and transmitted for each link service. The display application uses this information to control the flashing of the receive and transmit lights.  
  
  The other topics in this section describe the changes that must be made to the link service for supporting the modem status interface and the interface provided to the display application. Microsoft Host Integration Server comes with an application that displays the modem status.