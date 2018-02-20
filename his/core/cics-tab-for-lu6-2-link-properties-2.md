---
title: "CICS Tab (for LU6.2 Link Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15220"
ms.assetid: 680a647c-a843-4350-bb93-25c2a53c5dc1
caps.latest.revision: 3
robots: noindex,nofollow
---
# CICS Tab (for LU6.2 Link Properties)
Use the **CICS** tab to set host-specific CICS properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Transaction name**|Type or select the transaction name on CICS tied to CICS program DFHMIRS.|  
|**Allow use of explicit SYNCPOINT commands for non-transactional components**|Select this option to allow a CICS transaction program that is accessed as a nontransactional component to call EXEC CICS SYNCPOINT and EXEC CICS SYNCPOINT ROLLBACK commands.<br /><br /> Clear this option to make any CICS transactional component that calls SYNCPOINT commands fail with an ADPL CICS ABEND.<br /><br /> LU 6.2 Resync services must be configured on the SNA Local LU. Enable Sync Point must be enabled on SNA Remote LU. The Mode Table associated with the call must have sync level 2 enabled. The typelib must have transaction support properly set. The AppInt .Net model does not support Transactional nor does AppInt Com over TCP/IP.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [LU6.2 Tab (Remote Environment Properties)](../core/lu6-2-tab-remote-environment-properties-1.md)   
 [TI Manager Properties](../core/ti-manager-properties2.md)