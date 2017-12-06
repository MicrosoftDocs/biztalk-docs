---
title: "Registry Settings Used for LUA Single Sign-On1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e8a3bc2-0b52-4b82-b622-2facc47f95b4
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Registry Settings Used for LUA Single Sign-On
The logical unit application (LUA) Single Sign-On feature depends on [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] scanning 3270 logical units (LUs) used in the logon process for special keywords that are defined in the registry on the computer running [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)]. The values for these special keywords can be defined by the system administrator on the computer running [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)].  
  
 The registry settings used by the LUA Single Sign-On process are located under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** registry node. Installed under the **SNASERVR\PARAMETERS** subkey are the following entries:  
  
 **3270SSOPadByte**  
 This entry should be set to an ASCIIZ string to use as the character for padding replacement text in the user name or password if these strings are shorter than the length of the special tag strings. The default value for this pad character is the ASCII space character.  
  
 **3270SSOPostReplaceCount**  
 This entry should be set to a DWORD that represents the number of message chains of request/response units (RUs) to scan after replacement of text for user name or password. The default value for this number is 10.  
  
 **3270SSOPrefix**  
 This entry should be set to an ASCIIZ string to use as the special prefix tag string in combination with the user name and password tags. The default value of this string is MS$.  
  
 **3270SSOPwdTag**  
 This entry should be set to an ASCIIZ string to use as the special tag string in combination with the **3270SSOPrefix** tag in defining the special host password string that will be replaced. The default value of this string is SAMEP, so the default host password string that is scanned for and replaced is MS$SAMEP. Note that length of the password string that is scanned for (MS$SAMEP, for example) determines the maximum length of the password string that can sent to the host using Single Sign-On. This limit occurs because the password substitution cannot change the length of the data message. Note that the value of this string must be different from the value of the **3270SSOUserTag** entry for Single Sign-On to function properly.  
  
 **3270SSOReplaceCount**  
 A DWORD value that affects the time-out value for password substitution. User IDs and passwords will be substituted in each chain on the LU-SSCP and PLU-SLU sessions until the timer expires. By default the timer will be set to 30 seconds, but this behavior can be reconfigured in the registry using the **3270SSOReplaceCount** and **3270SSOReplaceTimer** registry entries. The timer is started when the OPEN SSCP is received by the node.  
  
 If the **3270SSOReplaceCount** registry entry is defined and the **3270SSOReplaceTimer** registry entry is not defined, the node counts this number of RUs (on PLU-SLU session only) before time-out occurs. If both the **3270SSOReplaceCount** and **3270SSOReplaceTimer** registry entries are defined, the value for **3270SSOReplaceCount** will be used to determine when a time-out will occur. By default, this key is not defined, and the node defaults to a time-out of 30 seconds.  
  
 **3270SSOReplaceTimer**  
 A DWORD value that affects the time-out value for password substitution. User IDs and passwords will be substituted in each chain on the LU-SSCP and PLU-SLU sessions until the timer expires. By default the timer will be set to 30 seconds, but this behavior can be reconfigured in the registry using the **3270SSOReplaceCount** and **3270SSOReplaceTimer** registry entries. The timer is started when the OPEN SSCP is received by the node.  
  
 If the **3270SSOReplaceTimer** registry entry is defined and **3270SSOReplaceCount** is not defined, the node uses this value in seconds before time-out occurs. If both the **3270SSOReplaceCount** and **3270SSOReplaceTimer** registry entries are defined, the value for **3270SSOReplaceCount** will be used to determine when a time-out will occur. By default, this key is not defined and the node defaults to a time-out of 30 seconds.  
  
 **3270SSOUserTag**  
 This entry should be set to an ASCIIZ string to use as the special tag string in combination with the **3270SSOPrefix** tag in defining the special user name string that will be replaced. The default value of this string is SAMEU, so the default user name string that is scanned for and replaced is MS$SAMEU. Note that length of the user name string that is scanned for (MS$SAMEU, for example) determines the maximum length of the user name string that can sent to the host using Single Sign-On. This limit occurs because the user name substitution cannot change the length of the data message. Note that the value of this string must be different from the value of the **3270SSOPwdTag** entry for Single Sign-On to function properly.