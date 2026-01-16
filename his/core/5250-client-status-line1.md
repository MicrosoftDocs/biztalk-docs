---
title: 5250 client status line
description: Learn more about the 5250 client status line.
ms.service: host-integration-server
ms.topic: concept-article
ms.date: 11/28/2023
---

# 5250 client status line

The following list describes the information displayed in the status line of the 5250 client:

- **Connection indicator**: The session is in either connected or disconnected state. When menu items are highlighted, an explanation of the menu item is displayed.

- **Status indicators**: These indicators are only true when red.

- **SA (System Available)**: The IBM i is operating and is available to the computer.

- **MW (Message Waiting)**: The IBM i has one or more messages for you.

- **KS (Keyboard Shift)**: The keyboard is in shifted mode.

- **IM (Insert Mode)**: Characters inserted into an existing field will not type over the existing data.

- **II (Input Inhibited)**: The IBM i isn't accepting keyboard input. Try pressing the ERROR RESET key. If still highlighted, the system is processing your request.

- **KB (Keystroke Buffering)**: The IBM i isn't accepting keyboard input, as indicated by the II indicator, so keystrokes are saved to a temporary buffer (storage space). After the II indicator turns off, the keystrokes are processed. To clear the keystroke buffering, press the ERROR RESET key.

- **System and Device Indicators**: These indicators appear only when the client is connected to the IBM i.

## See also  

[5250 Client](../core/5250-client1.md)
