---
title: "Logical Records Used in Basic Conversations2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d827d1d-e897-47d4-88c7-5fe75a4de319
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Logical Records Used in Basic Conversations
Logical records are sent and received in basic conversations only.  
  
 A TP can send or receive multiple logical records with a single [SEND_DATA](../Topic/SEND_DATA2.md) or receive verb. The receive verbs are [RECEIVE_AND_POST](../Topic/RECEIVE_AND_POST2.md), [RECEIVE_IMMEDIATE](../Topic/RECEIVE_IMMEDIATE2.md), and [RECEIVE_AND_WAIT](../Topic/RECEIVE_AND_WAIT1.md). A TP can also send or receive a logical record in successive portions: beginning, middle, and end.  
  
 A logical record is made up of:  
  
-   A 2-byte record-length (LL) field.  
  
-   A data field that can range in length from 0 bytes through 32765 bytes.  
  
 The LL field contains a hexadecimal value that is the length of the data field plus two bytes (for the LL field). For example, if a record contains 228 bytes of application data, the logical record length is 230. The LL field is 0x00E6, the hexadecimal equivalent of 230. If the length of the data field is 0, the value contained in the LL field is 0x0002.  
  
 Logical records are sent from or received in a data buffer established by the TP. In the data buffer, the LL field must not be in Intel byte-swapped format. For example, a length of 230 must be 0x00E6, not 0xE600.  
  
 The LL field cannot be 0x0000 or 0x0001, which allow less than the two bytes required for the LL field itself. The LL field also cannot be greater than or equal to 0x8000, which is equivalent to decimal 32768 and therefore allows for a data field greater than 32765 or an LL field greater than 2.  
  
 Setting the most significant bit of the LL field to 1 indicates that the information contained in the current logical record is continued in the next logical record.