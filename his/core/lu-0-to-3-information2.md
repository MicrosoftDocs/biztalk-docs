---
title: "LU 0 to 3 Information2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a8d5a8d-ce69-4937-aa11-30babc39e92e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# LU 0 to 3 Information
LU 0 to 3 information is provided in the **lu_0_3_info_sect** structure as defined below.  
  
## Syntax  
  
```  
typedef struct lu_0_3_info_sect {  
    unsigned long  lu_0_3_init_sect_len;  
    unsigned short num_lu_0_3s;  
} LU_0_3_ INFO_SECT;  
```  
  
## Members  
 lu_0_3_init_sect_len  
 The length of the initial LU 0 to 3 information section, including this parameter, up to the first link overlay group. The length does not include any previous information sections.  
  
 num_lu_0_3s  
 The number of LU groups. This is the number of times the lu_0_3 overlay group is repeated.  
  
 For each configured LU, an **lu_0_3_overlay** structure for the LU is provided as defined below.  
  
## Syntax  
  
```  
typedef struct lu_0_3_overlay {  
    unsigned long  lu_0_3_entry_len;  
    unsigned char  access_type;  
    unsigned char  lu_type;  
    unsigned char  lu_daf;  
    unsigned char  lu_short_name;  
    unsigned char  lu_long_name[8];  
    unsigned char  session_id[8];  
    unsigned long  dlc_name[8];  
    unsigned char  adapter_num;  
    unsigned char  dest_addr_len;  
    unsigned char  dest_addr[32];  
    unsigned char  sscp_lu_sess_state;  
    unsigned char  lu_lu_sess_state;  
    unsigned char  link_id[12];  
 } LU_0_3_OVERLAY;  
```  
  
## Defined by IBM ES for OS/2 version 1.0  
  
## Members  
 lu_0_3_entry_len  
 Size of this LU entry.  
  
 access_type  
 The access type (AP_3270 or AP_LUA).  
  
 lu_type  
 The LU type (AP_LU0, AP_LU1, AP_LU2, or AP_LU3).  
  
 lu_daf  
 The network addressable unit of the LU for which the information is displayed.  
  
 lu_short_name  
 The 1-byte LU short name (ASCII).  
  
 lu_long_name  
 The 8-byte ASCII LU long name.  
  
 session_id  
 The LU-LU session ID.  
  
 dlc_name  
 DLC name set to one of the following:  
  
 ETHERAND  
  IBMTRNET  
  IBMPCNET  
  SDLC  
  TWINAX (Not supported by Host Integration Server)  
  X25DLC  
  adapter_num  
 The DLC adapter number for host link.  
  
 dest_addr_len  
 Length of the destination adapter address.  
  
 dest_addr  
 The destination adapter address.  
  
 sscp_lu_sess_state  
 Specifies the state of the SSCP-LU session.  
  
 lu_lu_sess_state  
 Specifies the state of the LU-LU session. The state can be one of the following:  
  
 AP_NOT_BOUND  
 The LU-LU session is not bound.  
  
 AP_BOUND  
 The LU-LU session is bound.  
  
 AP_BINDING  
 The LU-LU session is in the process of binding.  
  
 AP_UNBINDING  
 The LU-LU session is in the process of unbinding.  
  
 link_id  
 Name of local logical link station being used.  
  
## Returned by Host Integration Server  
  
## Members  
 lu_0_3_entry_len  
 Size of this LU entry.  
  
 access_type  
 The access type (AP_3270 or AP_LUA).  
  
 lu_type  
 The LU type (AP_LU0, AP_LU1, AP_LU2, or AP_LU3).  
  
 lu_daf  
 The network addressable unit of the LU for which the information is displayed.  
  
 lu_short_name  
 The 1 byte ASCII LU short name.  
  
 lu_long_name  
 The 8 byte ASCII LU long name.  
  
 session_id  
 The LU-LU session ID.  
  
 dlc_name  
 DLC name set to one of the following:  
  
 IBMTRNET  
  SDLC  
  TWINAX (Not supported by Host Integration Server)  
  X25DLC  
  adapter_num  
 The DLC adapter number for host link. Always set to zero.  
  
 dest_addr_len  
 Length of the destination adapter address.  
  
 dest_addr  
 The destination adapter address.  
  
 sscp_lu_sess_state  
 Specifies the state of the SSCP-LU session.  
  
 lu_lu_sess_state  
 Specifies the state of the LU-LU session. The state can be one of the following:  
  
 AP_NOT_BOUND  
 The LU-LU session is not bound.  
  
 AP_BOUND  
 The LU-LU session is bound.  
  
 AP_BINDING  
 The LU-LU session is in the process of binding.  
  
 AP_UNBINDING  
 The LU-LU session is in the process of unbinding.  
  
 link_id  
 Name of connection.