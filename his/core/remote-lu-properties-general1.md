---
description: "Learn more about: Remote LU Properties: General"
title: "Remote LU Properties: General1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_LU_AppcRemote"
---
# Remote LU Properties: General
**Connection**  
 From the drop-down list, choose the connection that will be used to access this remote LU.  If a Local APPC LU is configured for dependent LU 6.2, this list will contain Host connections, which should be used for dependent LU 6.2 configuration.  
  
 **LU Alias**  
 Enter an LU Alias  
  
 **Network Name**  
 Enter a Network Name. Obtain the correct name from the host or peer administrator. If you will be connecting to a host system with VTAM, the Network Name for an APPC LU that communicates with a host should match the NETID parameter in the VTAM Start command for the VTAM system.  
  
 **LU Name**  
 Enter the LU Name.  
  
 A name identifying an LU. The name can be from one through eight characters long and can contain alphanumeric characters and the special characters $, #, and @. Lowercase letters are converted to uppercase. The name cannot be the same as any other LU name or pool name (except for APPC LU names) on the server.  
  
 For communication with an IBM i, make the remote LU name the same as the name of the IBM i.  
  
 **Uninterpreted LU Name**  
 If this LU will be paired with a dependent local APPC LU, type the Uninterpreted LU Name.  
  
 **Comment**  
 Optionally, enter a comment of not more than 25 characters.  
  
## Remote LU Properties: Options  
 **Supports Parallel Sessions**  
 If this LU will be used with an independent local LU, and parallel sessions will be used, select this check box. If this LU will be used with a dependent local APPC LU, do not select this box.  
  
 If a remote LU supports parallel sessions, it can only be used with a mode that has a value greater than 1 for the parallel session limit.  
  
 **Implicit Incoming Mode**  
 To designate a mode as the Implicit Incoming Mode for this LU, select a mode from the list.  
  
 If this remote LU will be used as an Implicit Incoming Mode be sure to select a mode from the list.  
  
 **No Session-Level Security**  
 Select this option to turn off Session-Level Security.  
  
 **Security Key in Hex**  
 For a security key in hexadecimal, select this option, then type a 16-digit hexadecimal number.  
  
 **Security Key in Characters**  
 For a security key in characters, select this option, then type an eight-character string. The string can include uppercase and lowercase alphanumeric characters, and the special characters $, @, #, and the period (.).  
  
 **Enable SyncPoint**  
 If you enable **SyncPoint**, the Local LU alias must be unique.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)
