---
title: "LUA User Name and Password Replacement1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc8f5b36-a727-4155-a1d0-89afb0707198
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# LUA User Name and Password Replacement
The SNA node on the host monitors the inbound session for a replacement sequence consisting of the **3270SSOPrefix** string immediately followed by one of the strings **3270SSOUserTag** or **3270SSOPwdTag**. Thus, the default user name string that would be scanned for and replaced is MS$SAMEU. When this string is found in the inbound session data, the node looks up the corresponding information (host user name in the Enterprise Single Sign-On (ESSO) database) and overwrites MS$SAMEU with this information. The same process occurs for the password string that would be scanned for and replaced, which defaults to MS$SAMEP.  
  
 Note that this operation cannot change the length of the data message. If the actual user name or password that is retrieved from the ESSO database is shorter than the replacement sequence, it is padded out with the first character of the **3270SSOPadByte** string used as a padding character. If the actual host user name or password string is longer than the string that is scanned for, these strings are truncated to the length of the scanned string so that the data message length is not affected.  
  
 Note that because the user name and password can be sent in any order, the registry string values for the **3270SSOUserTag** and **3270SSOPwdTag** entries must be different for Single Sign-On to function properly.  
  
 The SNA node monitors the SSCP-LU session for these special tag strings at all times and replaces all occurrences of these strings with corresponding looked-up data. On the LU-LU session, the node starts monitoring at start of session (BIND). The node stops monitoring when it has received **3270SSOPostReplaceCount** chains of request/response units (RUs) without seeing a substitution tag. The node will not restart monitoring until it receives an UNBIND–BIND sequence for that session.  
  
 Note that the node considers the sequence:  
  
```  
BIND, data, UNBIND(BIND FORTHCOMING), BIND       
```  
  
 as a continuation of the same LU-LU session and does not restart monitoring on receipt of the second BIND. This sequence is often used by host session managers handing off a session to an application system, and is considered a single terminal session.  
  
 User IDs and passwords will be substituted in each chain on the LU-SSCP and PLU-SLU sessions until the node has received **3270SSOPostReplaceCount** chains of RUs without seeing a substitution tag or a timer expires. By default the timer is set to 30 seconds, but this behavior can be reconfigured in the registry using the **3270SSOReplaceCount** and **3270SSOReplaceTimer** registry entries. The timer is started when the OPEN SSCP is received by the node. After the timer expires, the node will stop scanning messages for the 3270 replacements strings for the user ID and password. If the replacement strings arrive after the timer expires, the replacement strings will be sent to the host unmodified causing the sign-on to fail. The application will not receive any notification that the timer has expired. The only indication of a problem will likely be that the sign-on to the host session has failed.  
  
> [!NOTE]
>  All strings are specified in the registry in ASCII, but the node translates them to EBCDIC through AE character mapping before scanning for a match.