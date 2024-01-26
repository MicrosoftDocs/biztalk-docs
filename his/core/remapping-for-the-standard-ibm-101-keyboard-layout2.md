---
description: "Learn more about: Remapping for the Standard IBM 101 Keyboard Layout"
title: "Remapping for the Standard IBM 101 Keyboard Layout2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Remapping for the Standard IBM 101 Keyboard Layout
When using the Host Integration Server 5250 Client, function keys located on the numeric keypad (such as PGUP, PGDN and ENTER) are not mapped to 5250 functions for PAGE UP, PAGE DOWN, and ENTER. The standard cursor control keys for PageUp and PageDown (located on the keypad positioned between the BACKSPACE and NUMLOCK keys) and the standard ENTER key do work.  
  
 The \<Snaroot>\System\5250.kbd file can be edited to support limited keyboard remapping, for the standard IBM 101 keyboard layout. For example, the procedure below describes how to add support for the ENTER, PGUP and PGDN keys located on the numeric keypad:  
  
 **To add support for the ENTER, PGUP and PGDN keys**  
  
1.  Save the original copy of \<Snaroot>\System\5250.kbd to 5250.old.  
  
2.  Add the following lines to the 5250.kbd file:  
  
    -   NumPgUp : PAGE_UP  
  
    -   NumPgDn : PAGE_DOWN  
  
    -   NumEnter: ENTER  
  
> [!NOTE]
>  5250.kbd will already include default entries for the 5250 PAGE_UP, PAGE_DOWN, and ENTER functions, mapped to the PAGEUP, PAGEDOWN, and ENTER keys respectively.  
  
1.  . Restart the 5250 Client.  
  
> [!NOTE]
>  The Host Integration Server 5250 Client does support limited keyboard remapping by following the instructions in the \<Snaroot>\System\5250.kbd file. This keyboard mapping support is not available in SNA Server 2.x versions of the 5250 Client.  
  
## See Also  
 [5250 Client](../core/5250-client1.md)
