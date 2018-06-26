---
title: "Local LU Properties: General1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_LU_AppcLocal"
ms.assetid: 7b4087aa-b3d8-4531-86a4-03c257457151
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Local LU Properties: General
Local APPC LUs can be independent or dependent.  
  
 **LU Alias**  
 Enter the LU Alias.  
  
 **Network Name**  
 Type the Network Name. Obtain the correct name from the host or peer administrator if you will be connecting to a host system with VTAM,  
  
 The Network Name for an APPC LU that communicates with a host should match the NETID parameter in the VTAM Start command for the VTAM system.  
  
 If this server communicates with several different hosts over several connections, use the name of the subarea of the host with which the LU will communicate.  
  
 For independent LUs, the Network Name is required. For dependent LUs, the Network Name is recommended but not required, since it is used only by local software, such as the Windows event log software.  
  
 **LU Name**  
 Enter the LU Name. For independent APPC, the LU Name identifies the LU to other components on the SNA network, and therefore is required. For dependent APPC, the LU Name identifies the LU to local software, such as the Windows event log software, and is recommended but not required.  
  
 The LU Name and LU Alias for an APPC LU can be the same.  
  
 **Comment**  
 Optionally, enter a comment of no more than 25 characters.  
  
## Local LU Properties: Advanced  
 **Member of Default Outgoing Local APPC LU Pool**  
 If you want this LU to be available for use by a 5250 user or invoking TP not specifying a local LU, select this check box.  
  
 When a request comes from an invoking TP, and the request does not specify a local LU for the invoking TP to use, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] first checks the user record of the user who started the TP, and tries to use the default local APPC LU assigned to that user or group. If this does not succeed, Host Integration Server tries to find a free LU in the pool of Default Outgoing Local APPC LUs. If this in turn does not succeed, the request is rejected.  
  
 Local LUs only support the number of sessions configured for the mode being used. The default for QPCSUPP is 64 sessions. If you need more than that number of sessions, then you need to configure multiple local LUs or increase the session limits in the mode definition for each mode used. To simplify user configuration, you can make all of these local APPC LUs part of the default pool by checking the **Member of Default Outgoing Local LU Pool.** This allows any user who does not specify a local APPC LU to get an available session from any local APPC LU in the default pool. This also enables load balancing among local APPC LUs. In addition, to ensure proper load balancing, do not specify a **Default Local LU Alias** for users or groups. However, if you want to have certain users or groups default to a certain local APPC LU, then you should specify that local APPC LU as the **Default Local LU Alias** in the user or group properties.  
  
 This default pool differs from, and should not be confused with, the 3270, LUA, and downstream LU pools.  
  
 **Timeout for Starting Invokable TPs**  
 If the **Invokable TP** is started manually by an operator, specify a value greater than 60 seconds to give the operator sufficient time.  
  
 **Implicit Incoming Remote LU**  
 To specify an Implicit incoming remote LU, choose an existing remote LU name from the list.  
  
 **LU 6.2 Type**  
 Select **Independent** or **Dependent**.  
  
 **LU Number**  
 For dependent LUs, enter the LU Number.  
  
 For independent LUs, this field is unavailable.  
  
 **Connection**  
 For **Dependent LU**s, choose the connection from the drop-down list.  
  
 For **Independent LU**s, this field is unavailable.  
  
### LU 6.2 Resync Service  
 **Computer**  
 Type the **IP Address** or the **Name** of the client computer. The client computer specifies a system that is dedicated in that the LU routes incoming connections to that client computer.  
  
 Check the **Enable** box if you have a very specialized transaction program (TP) that requires Resync Service. Resync Service or SyncPoint support is used by some database management systems (DBMS) for commit and rollback procedures. If you enable this service, the Local LU alias must be unique.  
  
 If you have multiple local and remote LUs using two-phase commit, you may want to explicitly partner the LUs. This will prevent the Resync Service from attempting to bind invalid LU pairs.  
  
 **To explicitly partner LUs**  
  
1. In **SNA Manager**, click the **APPC Modes** folder.  
  
2. Right-click **RSYNPRTN**, and then click **Properties**.  
  
3. Select the **Partner** tab.  
  
4. Click **Add**, and then follow the directions in the dialog box.  
  
   If you would like the Resync Service to use a different mode name, you can specify a new name with the following registry key:  
  
   HKLM\Software\Microsoft\Host Integration Server\UN2  
  
   REG_SZ: modename  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)