---
title: "Link Definition Information2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e93454d-2e8e-4d5b-8339-8f0d2003ddbe
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Link Definition Information
Link definition information is provided in the **link_def_info_sect** structure as defined below.  
  
## Syntax  
  
```  
typedef struct link_def_info_sect {  
    unsigned long  link_def_init_sect_len;  
    unsigned short num_link_def;  
    unsigned short total_link_def;  
} LINK_DEF_INFO_SECT;  
```  
  
## Members  
 link_def_init_sect_len  
 The length of the initial link definition information section, including this parameter, up to the first link definition overlay group. The length does not include any previous information sections.  
  
 num_link_def  
 The number of link definitions returned by the **DISPLAY** verb into your program's buffer. This is the number of times the link definition overlay is repeated.  
  
 total_link_def  
 The total number of link definitions. This number is the same as the number returned in the **num_link_def** member except when APPC has more information about link definitions than it can place in the supplied buffer, in which case this number is larger.  
  
 For each link definition, a **link_def_overlay** structure for the link definition is provided as defined below.  
  
## Syntax  
  
```  
typedef struct link_def_overlay {  
    unsigned long  link_def_entry_len;  
    unsigned char  link_name[8];  
    unsigned char  adj_fq_cp_name[17];  
    unsigned char  adj_node_type;  
    unsigned long  dlc_name[8];  
    unsigned char  adapter_num;  
    unsigned char  dest_addr_len;  
    unsigned char  dest_addr[32];  
    unsigned char  preferred_nn_server;  
    unsigned char  auto_act_link;  
    unsigned char  tg_number;  
    unsigned char  lim_res;  
    unsigned char  solicit_sscp_session;  
    unsigned char  initself;  
    unsigned char  bind_support;  
    unsigned char  ls_role;  
    unsigned char  line_type;  
    unsigned long  eff_capacity;  
    unsigned char  conn_cost;  
    unsigned char  byte_cost;  
    unsigned char  propagation_delay;  
    unsigned char  user_def_1;  
    unsigned char  user_def_2;  
    unsigned char  user_def_3;  
    unsigned char  security;  
    unsigned char  reserv;  
 } LINK_OVERLAY;  
```  
  
## Defined by IBM ES for OS/2 version 1.0  
  
## Members  
 link_def_entry_len  
 Size of this link definition entry.  
  
 link_name  
 Local logical link station name (EBCDIC).  
  
 dlc_name  
 Data link control (DLC) name set to one of the following:  
  
 ETHERAND  
  IBMTRNET  
  IBMPCNET  
  SDLC  
  TWINAX (Not supported by Host Integration Server)  
  X25DLC  
  adj_fq_cp_name  
 Fully qualified **cp_name** in adjacent node.  
  
 adj_node_type  
 The adjacent node type (AP_ADJACENT_NN, AP_LEARN, or AP_LEN).  
  
 adapter_num  
 DLC adapter number used by this link.  
  
 dest_addr_len  
 Length of the destination adapter address.  
  
 dest_addr  
 The destination adapter address.  
  
 cp_cp_sess_spt  
 Specifies whether the link supports CP-CP sessions.  
  
 preferred_nn_server  
 Indicates if this is the preferred NN server.  
  
 auto_act_link  
 Indicates if the link should be automatically activated.  
  
 tg_number  
 Transmission group number.  
  
 lim_res  
 Indicates if this is a limited resource.  
  
 solicit_sscp_session  
 Indicates whether to solicit an SSCP session.  
  
 initself  
 Indicates if the node supports receiving INIT_SELF over this link.  
  
 bind_support  
 Indicates whether BIND support is available.  
  
 ls_role  
 Specifies the link station role.  
  
 line_type  
 The line type.  
  
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
  
## Returned by Host Integration Server  
  
## Members  
 link_def_entry_len  
 Size of this link definition entry.  
  
 link_name  
 Local logical link station name (EBCDIC).  
  
 dlc_name  
 Data link control (DLC) name set to one of the following:  
  
 IBMTRNET  
  SDLC  
  X25DLC  
  adj_fq_cp_name  
 Fully qualified **cp_name** in adjacent node. Always set to EBCDIC spaces.  
  
 adj_node_type  
 The adjacent node type. Always set to AP_LEN.  
  
 adapter_num  
 DLC adapter number used by this link. Always set to zero.  
  
 dest_addr_len  
 Length of the destination adapter address.  
  
 dest_addr  
 The destination adapter address.  
  
 cp_cp_sess_spt  
 Specifies whether the link supports CP-CP sessions. Always set to AP_NO.  
  
 preferred_nn_server  
 Indicates if this is the preferred NN server.  
  
 auto_act_link  
 Indicates if the link should be automatically activated.  
  
 tg_number  
 Transmission group number. Always set to zero.  
  
 lim_res  
 Indicates if this is a limited resource.  
  
 solicit_sscp_session  
 Indicates whether to solicit an SSCP session.  
  
 initself  
 Indicates if the node supports receiving INIT_SELF over this link.  
  
 bind_support  
 Indicates whether BIND support is available.  
  
 ls_role  
 Specifies the link station role.  
  
 line_type  
 The line type.  
  
 effective_capacity  
 Highest bit rate transmission effective capacity supported. Always set to zero.  
  
 conn_cost  
 Relative cost per connection time using this link. Always set to zero.  
  
 byte_cost  
 Relative cost of transmitting a byte over link. Always set to zero.  
  
 propagation_delay  
 Indicates amount of time for signal to travel length of link. Set to one of the following: Always set to AP_PROP_DELAY_MAXIMUM.  
  
 user_def_1  
 User-defined TG characteristics. Always set to zero.  
  
 user_def_2  
 User-defined TG characteristics. Always set to zero.  
  
 user_def_3  
 User-defined TG characteristics. Always set to zero.  
  
 security  
 The security value for this link. Always set to AP_SEC_NONSECURE.