---
title: "OIA Inidcators1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74d5d11f-c9ae-4141-92e5-38d051c89935
caps.latest.revision: 4
---
# OIA Inidcators
The Operator Information Area (OIA) is used to display the status of a 3270 screen session. The OIA is the last (bottom) line display in the terminal window of the 3270 session. Except for the initial three positions (system connection indicators), status line indicators only appear when they apply.  
  
 The following tables describe the OIA and explain each indicator. In the table, position refers to the column(s) that a specific indicator occupies on the OIA, where the left-most column of the OIA is position 1. Note that the "female" symbol used for certain system connection and input-inhibited indicators cannot be displayed in this table. In its place is the "^" symbol.  
  
 Following is a list of symbols found on each system connection and their respective meanings.  
  
 **System Connection (position 1)**  
  
 Does not apply to Host Integration Server 3270 Client.  
  
 **System Connection (position 2)**  
  
 **B** Connection uses an SNA protocol.  
  
 **A** Connection uses a non-SNA protocol.  
  
 **System Connection (position 3)**  
  
 **b** Connected to a host application (LU-LU session).  
  
 **^** Connected to host system services (SSCP-LU session).  
  
 **?** Session is established, but is not connected to any host program (unknown).  
  
 **Session ID (positions 4-7)**  
  
 **aaaa** First four characters of your configured long name session ID.  
  
 **Input-Inhibited messages (keyboard locked) (positions 9-17)**  
  
 **X COMMnnn** Communications error. See Communications Status (positions 19-26).  
  
 **X MACHnnn** Machine check error.  
  
 **X PROGnnn** Program check error. See Communications Status (positions 19-26).  
  
 **X SYSTEM** Keyboard input is being processed by the host. Wait for the message to clear or press RESET.  
  
 **X[]** The host requires more time to process your request. Wait for indicator to clear or press RESET.  
  
 **X -f** Function is not supported. Press RESET and select a valid function.  
  
 **X^>** More data was typed than the field allows or can accept. Press RESET and re-enter the data.  
  
 **X \<-^->** Protected field; you cannot type data. Press RESET and move the cursor to an unprotected field.  
  
 **X -f^X** Function is not authorized. Press RESET and select a valid function.  
  
 **X^+?** Invalid accent/character combination typed. The accent is displayed in position 12. Press RESET and type a valid combination.  
  
 **Communications Status (positions 19-26)**  
  
 **COMM500** All the link services configured for use by the connection were inactive.  
  
 **COMM504** Communications are not established with the host. This message disappears as soon as communication is established with the host. If this message does not disappear, check to ensure proper settings of the host network address, local node ID, or local SAP.  
  
 **COMM505** The host terminated the connection used by your 3270 session.  
  
 **COMM510** The host has deactivated the communications link. Report the message to your system administrator.  
  
 **COMM518** A segment was out of sequence. Contact your system administrator.  
  
 **COMM695** A communications error occurred.  
  
 **COMM5nn** The communications link is still being established; the keyboard is locked. Wait for the message to clear; also check Input-Inhibited messages.  
  
 **PROG703** A session control, data flow control or network control command is not supported. Press RESET, and try the operation again.  
  
 **PROG705** A sequence number error has occurred. Press RESET, and try the operation again.  
  
 **PROG706** A chaining error has occurred. Press RESET, and try the operation again.  
  
 **PROG707** A bracket state error has occurred. Press RESET, and try the operation again.  
  
 **PROG708** A data traffic reset state exists. Press RESET and try the operation again.  
  
 **PROG717** The support level requested is not valid. Press RESET, and try the operation again.  
  
 **PROG723** The LU type requested is not valid. Press RESET, and try the operation again.  
  
 **PROG724** The screen size requested is not valid. Press RESET, and try the operation again.  
  
 **Screen Session LU Address (positions 79-80)**  
  
 **Nn** The LU address of the currently displayed 3270 screen session.  
  
## See Also  
 [3270 Client](../core/3270-client1.md)