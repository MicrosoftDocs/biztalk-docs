---
title: "Active Link Information2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 902cee90-5484-4f72-8aa7-35dc19736a80
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Active Link Information
Active link information is provided in the **link_info_sect** structure as defined below.  
  
## Syntax  
  
```  
typedef struct link_info_sect {  
    unsigned long  link_init_sect_len;  
    unsigned short num_links;  
    unsigned short total_links;  
} LINK_INFO_SECT;  
```  
  
## Members  
 link_init_sect_len  
 The length of the initial active link information section, including this parameter, up to the first link overlay group. The length does not include any previous information sections.  
  
 num_links  
 The number of active links returned by the **DISPLAY** verb into your program's buffer. This is the number of times the link overlay group is repeated.  
  
 total_links  
 The total number of active links. This number is the same as the number returned in the **num_links** member except when APPC has more information about active links than it can place in the supplied buffer, in which case this number is larger.  
  
 For each active link, a **link_overlay** structure for the active link is provided as defined below.  
  
## Syntax  
  
```  
typedef struct link_overlay {  
    unsigned long  link_entry_len;  
    unsigned char  link_id[12];  
    unsigned long  dlc_name[8];  
    unsigned char  adapter_num;  
    unsigned char  dest_addr_len;  
    unsigned char  dest_addr[32];  
    unsigned char  inbound_outbound;  
    unsigned char  state;  
    unsigned char  deact_link_flag;  
    unsigned char  reserv3;  
    unsigned short num_sessions;  
    unsigned short ru_size;  
    unsigned short reserv4;  
    unsigned char  adj_fq_cp_name[17];  
    unsigned char  adj_node_type;  
    unsigned char  reserv5;  
    unsigned char  cp_cp_sess_spt;  
    unsigned char  conn_type;  
    unsigned char  ls_role;  
    unsigned char  line_type;  
    unsigned char  tg_number;  
    unsigned long  eff_capacity;  
    unsigned char  conn_cost;  
    unsigned char  byte_cost;  
    unsigned char  propagation_delay;  
    unsigned char  user_def_1;  
    unsigned char  user_def_2;  
    unsigned char  user_def_3;  
    unsigned char  security;  
    unsigned char  reserv6;  
 } LINK_OVERLAY;  
```  
  
## Defined by IBM ES for OS/2 version 1.0  
  
## Members  
 link_entry_len  
 Size of this link entry.  
  
 link_id  
 Local logical link station name (EBCDIC).  
  
 dlc_name  
 Data link control (DLC) name set to one of the following:  
  
 ETHERAND  
  IBMTRNET  
  IBMPCNET  
  SDLC  
  TWINAX (Not supported by [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)])  
  X25DLC  
  adapter_num  
 Adapter number used by this link to connect to the adjacent node.  
  
 dest_addr_len  
 Length of the destination adapter address.  
  
 dest_addr  
 The destination adapter address.  
  
 inbound_outbound  
 The direction of the link.  Values can be:  
  
 AP_OUTBOUND  
 The link is outbound.  
  
 AP_INBOUND  
 The link is inbound.  
  
 state  
 The state of the link. The link state can be one of the following:  
  
 AP_CONALS_PND  
 The process to bring up the link has started but XID negotiation has not started.  
  
 AP_XID_PND  
 XID negotiation is in process.  
  
 AP_CONTACT_PND  
 XID negotiation has been completed but the final response from the DLC has not been received.  
  
 AP_CONTACTED  
 The link is fully functioning.  
  
 AP_DISC_PND  
 A request to disconnect the link has been issued to the DLC.  
  
 AP_DISC_RQ  
 The operator has requested that the link be disconnected.  
  
 deact_link_flag  
 Deactivate logical link.  
  
 reserv3  
 A reserved field.  
  
 num_sessions  
 Number of active sessions.  
  
 ru_size  
 RU size.  
  
 reserv4  
 A reserved field.  
  
 adj_fq_cp_name  
 Fully qualified **cp_name** in adjacent node.  
  
 adj_node_type  
 The adjacent node type (NN, EN, or LEN).  
  
 cp_cp_sess_spt  
 Specifies whether the link supports CP-CP sessions.  
  
 conn_type  
 Indicates whether the session activation protocol follows the rules for an independent LU or a dependent LU. The connection type can be one of the following:  
  
 AP_HOST_SESSION  
 For dependent LU protocols, the workstation LU is defined as dependent at the host, the host LU sends the session activation request (BIND), and each workstation LU can support only one session at a time.  
  
 AP_PEER_SESSION  
 For independent LU protocols, an LU can send a BIND, and can have multiple sessions to different partners, or parallel sessions to the same partner LU.  
  
 AP_BOTH_SESSION  
 Connections can support both Dependent and Independent LUs.  
  
 ls_role  
 Specifies the link station role.  
  
 line_type  
 The line type.  
  
 tg_number  
 Transmission group number.  
  
 eff_capacity  
 Highest bit rate transmission effective capacity supported.  
  
 conn_cost  
 Relative cost per connection time using this link.  
  
 byte_cost  
 Relative cost of transmitting a byte over link.  
  
 propagation_delay  
 Indicates amount of time for signal to travel length of link. Set to one of the following:  
  
 AP_PROP_DELAY_MINIMUM  
  AP_PROP_DELAY_LAN  
  AP_PROP_DELAY_TELEPHONE  
  AP_PROP_DELAY_PKT_SWITCHED_NET  
  AP_PROP_DELAY_SATELLITE  
  AP_PROP_DELAY_MAXIMUM  
  user_def_1  
 User-defined TG characteristics.  
  
 user_def_2  
 User-defined TG characteristics.  
  
 user_def_3  
 User-defined TG characteristics.  
  
 security  
 The security value for this link. Set to one of the following:  
  
 AP_SEC_NONSECURE  
  AP_SEC_PUBLIC_SWITCHED_NETWORK  
  AP_SEC_UNDERGROUND_CABLE  
  AP_SEC_SECURE_CONDUIT  
  AP_SEC_GUARDED_CONDUIT  
  AP_SEC_ENCRYPTED  
  AP_SEC_GUARDED_RADIATION  
  reserv6  
 A reserved field.  
  
## Returned by Host Integration Server  
  
## Members  
 link_entry_len  
 Size of this link entry.  
  
 link_id  
 Connection name.  
  
 dlc_name  
 DLC name set to one of the following:  
  
 IBMTRNET  
  SDLC  
  X25DLC  
  adapter_num  
 Adapter number used by this link to connect to the adjacent node. Always set to zero.  
  
 dest_addr_len  
 Length of the destination adapter address.  
  
 dest_addr  
 The destination adapter address.  
  
 inbound_outbound  
 The direction of the link.  Values can be:  
  
 AP_OUTBOUND  
 The link is outbound.  
  
 AP_INBOUND  
 The link is inbound.  
  
 state  
 The state of the link. The link state can be one of the following:  
  
 AP_CONALS_PND  
 The process to bring up the link has started but XID negotiation has not started.  
  
 AP_XID_PND  
 XID negotiation is in process.  
  
 AP_CONTACT_PND  
 XID negotiation has been completed but the final response from the DLC has not been received.  
  
 AP_CONTACTED  
 The link is fully functioning.  
  
 AP_DISC_PND  
 A request to disconnect the link has been issued to the DLC.  
  
 AP_DISC_RQ  
 The operator has requested that the link be disconnected.  
  
 deact_link_flag  
 Deactivate logical link.  
  
 num_sessions  
 Number of active sessions.  
  
 ru_size  
 RU size.  
  
 adj_fq_cp_name  
 Fully qualified **cp_name** in adjacent node. Always set to EBCDIC spaces.  
  
 adj_node_type  
 The adjacent node type. Always set to AP_LEN.  
  
 cp_cp_sess_spt  
 Specifies whether the link supports CP-CP sessions. Always set to AP_NO.  
  
 conn_type  
 Indicates whether the session activation protocol follows the rules for an independent LU or a dependent LU. The connection type can be one of the following:  
  
 AP_HOST_SESSION  
 For dependent LU protocols, the workstation LU is defined as dependent at the host, the host LU sends the session activation request (BIND), and each workstation LU can support only one session at a time.  
  
 AP_PEER_SESSION  
 For independent LU protocols, an LU can send a BIND, and can have multiple sessions to different partners, or parallel sessions to the same partner LU.  
  
 ls_role  
 Specifies the link station role.  
  
 line_type  
 The line type.  
  
 tg_number  
 Transmission group number. Always set to zero.  
  
 effective_capacity  
 Highest bit rate transmission effective capacity supported. Always set to zero.  
  
 conn_cost  
 Relative cost per connection time using this link. Always set to zero.  
  
 byte_cost  
 Relative cost of transmitting a byte over link. Always set to zero.  
  
 propagation_delay  
 Indicates amount of time for signal to travel length of link. This parameter is always set to AP_PROP_DELAY_MAXIMUM.  
  
 user_def_1  
 User-defined TG characteristics. Always set to zero.  
  
 user_def_2  
 User-defined TG characteristics. Always set to zero.  
  
 user_def_3  
 User-defined TG characteristics. Always set to zero.  
  
 security  
 The security value for this link. Always set to AP_SEC_NONSECURE.