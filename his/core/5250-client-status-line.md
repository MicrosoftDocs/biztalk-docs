---
title: "5250 Client Status Line1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41ceb93b-3ade-4660-9f01-12eae2841ae3
caps.latest.revision: 4
---
# 5250 Client Status Line
The following list describes the information displayed in the status line of the 5250 Client.  
  
 **Connection Indicator** The session is in the indicated state: connected or disconnected. When menu items are highlighted, an explanation of the menu item is displayed.  
  
 **Status Indicators** These indicators are only true when red.  
  
 **SA (System Available)** The AS/400 is operating and is available to the computer.  
  
 **MW (Message Waiting)** The AS/400 has one or more messages for you.  
  
 **KS (Keyboard Shift)** The keyboard is in shifted mode.  
  
 **IM (Insert Mode)** Characters inserted into an existing field will not type over the existing data.  
  
 **II (Input Inhibited)** Keyboard input is not being accepted by the AS/400. Try pressing the ERROR RESET key. If it is still highlighted, the system is processing your request.  
  
 **KB (Keystroke Buffering)** Keystrokes are being saved in a temporary buffer (storage space), because keyboard input is not being accepted by the AS/400 (as indicated by the II indicator). After the II indicator goes off, the keystrokes will be processed. To clear the keystroke buffering, press the ERROR RESET key.  
  
 **System and Device Indicators** These indicators appear only when the Client is connected to the AS/400.  
  
## See Also  
 [5250 Client](../core/5250-client.md)