---
title: "Session Information1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ba628bf-dfb2-4242-92ff-743d8d48a431
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Session Information
Information on session information is provided in the **sess_info_sect** structure as defined below.  
  
## Syntax  
  
```  
typedef struct sess_info_sect {  
    unsigned long  sess_sect_len;  
    unsigned short num_sessions;  
    unsigned short total_sessions;  
} SESS_INFO_SECT;  
```  
  
## Members  
 sess_sect_len  
 The length of the initial session information section, including this parameter, up to the first session group. The length does not include any previous information sections.  
  
 num_sessions  
 The number of session groups returned by the **DISPLAY** verb into your program's buffer. This is the number of times the session group is repeated.  
  
 total_sessions  
 The total number of session groups. This number is the same as the number returned in the **num_sessions** member except when APPC has more information about session groups than it can place in the supplied buffer, in which case this number is larger.  
  
 For each session group, a **sess_overlay** structure for the session is provided as defined below.  
  
## Syntax  
  
```  
typedef struct sess_overlay {  
    unsigned long  sess_entry_len;  
    unsigned long  reserv3;  
    unsigned char  sess_id[8];  
    unsigned long  conv_id[8];  
    unsigned char  lu_alias[8];  
    unsigned char  plu_alias[8];  
    unsigned char  mode_name[8];  
    unsigned short send_ru_size;  
    unsigned short rcv_ru_size;  
    unsigned short send_pacing_size;  
    unsigned short rcv_pacing_size;  
    unsigned char  link_id[12];  
    unsigned char  daf;  
    unsigned char  oaf;  
    unsigned char  odai;  
    unsigned char  sess_type;  
    unsigned char  conn_type;  
    unsigned char  reserv4;  
    FPCID_OVERLAY  fpcid;  
    unsigned char  cgid[4];  
    unsigned char  fqlu_name[17];  
    unsigned char  fqplu_name[17];  
    unsigned char  pacing_type;  
    unsigned char  reserv5;  
 } SESS_OVERLAY;  
```  
  
## Defined by IBM ES for OS/2 version 1.0  
  
## Members  
 sess_entry_len  
 Size of this session group entry.  
  
 sess_id  
 The internal identifier of the session for which this information is displayed.  
  
 conv_id  
 The unique four-byte ID of the conversation currently using this session.  
  
 lu_alias  
 LU alias (ASCII).  
  
 plu_alias  
 Partner LU alias (ASCII).  
  
 mode_name  
 The name of the mode (EBCDIC).  
  
 send_ru_size  
 The maximum RU size used on this session and this **mode_name** for sending RUs.  
  
 rcv_ru_size  
 The maximum RU size used on this session and this **mode_name** for receiving RUs.  
  
 send_pacing_size  
 The size of the send pacing window on this session.  
  
 rcv_pacing_size  
 The size of the receive pacing window on this session.  
  
 link_id  
 Name of local logical link station.  
  
 daf  
 The destination address field for this session.  
  
 oaf  
 The origin address field for this session.  
  
 odai  
 The origin destination address indicator field for this session.  
  
 sess_type  
 The type of the session. The session type can be one of the following:  
  
 SSCP_PU_SESSION  
 This session is between a workstation physical unit and a host system services control point. This type of session exists if the local node contains a dependent LU, or if the session has been solicited in order to send alerts to the host.  
  
 SSCP_LU_SESSION  
 This session is between a dependent LU and a host system services control point.  
  
 LU_LU _SESSION  
 This session is between two LUs.  
  
 conn_type  
 Indicates whether the session activation protocol follows the rules for an independent LU or a dependent LU. The connection type can be one of the following:  
  
 AP_HOST_SESSION  
 For dependent LU protocols, the workstation LU is defined as dependent at the host, the host LU sends the session activation request (BIND), and each workstation LU can support only one session at a time.  
  
 AP_PEER_SESSION  
 For independent LU protocols, an LU can send a BIND, and can have multiple sessions to different partners, or parallel sessions to the same partner LU.  
  
 fq_pc_id  
 Fully qualified procedure correlation identifier of the session.  
  
 cgid  
 Unique identifier for the conversation group of the session.  
  
 fqlu_name  
 The fully-qualified LU name in EBCDIC (type A).  
  
 fqplu_name  
 The fully-qualified partner LU name in EBCDIC (type A).  
  
 pacing_type  
 The pacing type can be one of the following:  
  
 AP_FIXED  
 Fixed pacing.  
  
 AP_ADAPTIVE  
 Adaptive pacing.  
  
## Returned by Host Integration Server  
  
## Members  
 sess_entry_len  
 Size of this session group entry.  
  
 sess_id  
 The internal identifier of the session for which this information is displayed.  
  
 conv_id  
 The unique four-byte ID of the conversation currently using this session.  
  
 lu_alias  
 LU alias (ASCII).  
  
 plu_alias  
 Partner LU alias (ASCII).  
  
 mode_name  
 The name of the mode (EBCDIC).  
  
 mode_name  
 The name of the mode (EBCDIC).  
  
 send_ru_size  
 The maximum RU size used on this session and this **mode_name** for sending RUs.  
  
 rcv_ru_size  
 The maximum RU size used on this session and this **mode_name** for receiving RUs.  
  
 send_pacing_size  
 The size of the send pacing window on this session.  
  
 rcv_pacing_size  
 The size of the receive pacing window on this session.  
  
 link_id  
 Connection name.  
  
 daf  
 The destination address field for this session.  
  
 oaf  
 The origin address field for this session.  
  
 odai  
 The origin destination address indicator field for this session.  
  
 sess_type  
 The type of the session. The session type can be one of the following:  
  
 SSCP_PU_SESSION  
 This session is between a workstation physical unit and a host system services control point. This value is never returned by Host Integration Server.  
  
 SSCP_LU_SESSION  
 This session is between a dependent LU and a host system services control point.  
  
 LU_LU _SESSION  
 This session is between two LUs.  
  
 conn_type  
 Indicates whether the session activation protocol follows the rules for an independent LU or a dependent LU. The connection type can be one of the following:  
  
 AP_HOST_SESSION  
 For dependent LU protocols, the workstation LU is defined as dependent at the host, the host LU sends the session activation request (BIND), and each workstation LU can support only one session at a time.  
  
 AP_PEER_SESSION  
 For independent LU protocols, an LU can send a BIND, and can have multiple sessions to different partners, or parallel sessions to the same partner LU.  
  
 AP_BOTH_SESSION  
 Connections can support both Dependent and Independent LUs.  
  
 fq_pc_id  
 Set to zero.  
  
 cgid  
 Set to zero.  
  
 type_of_pacing  
 The pacing type can be one of the following:  
  
 AP_FIXED  
 Fixed pacing.  
  
 AP_ADAPTIVE  
 Adaptive pacing. This value is never returned by Host Integration Server.