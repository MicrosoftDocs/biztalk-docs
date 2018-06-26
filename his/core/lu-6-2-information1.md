---
title: "LU 6.2 Information1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8bab4dc-80a0-424d-8550-85c7ec5f449a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# LU 6.2 Information
Information on LUs is provided in the **lu62_info_sect** structure as defined below.  
  
## Syntax  
  
```  
typedef struct lu62_info_sect {  
    unsigned long  lu62_init_sect_len;  
    unsigned short num_lu62s;  
    unsigned short total_lu62s;  
} LU62_INFO_SECT;  
```  
  
## Members  
 lu62_init_sect_len  
 Structure length.  
  
 num_lu62s  
 Number of configured LUs displayed.  
  
 total_lu62s  
 Total number of configured LUs.  
  
 For each configured LU, an **lu62_overlay** structure is provided as defined below.  
  
## Syntax  
  
```  
typedef struct lu62_overlay {  
    unsigned long  lu62_entry_len;  
    unsigned long  lu62_overlay_len;  
    unsigned char  lu_name[8];  
    unsigned char  lu_alias[8];  
    unsigned short num_plus;  
    unsigned char  fqlu_name[17];  
    unsigned char  default_lu;  
    unsigned char  reserv3;  
    unsigned char  lu_local_addr;  
    unsigned short lu_sess_lim;  
    unsigned char  max_tps;  
    unsigned char  lu_type;  
} LU62_OVERLAY;  
```  
  
## Members  
 lu62_entry_len  
 Size of this LU entry.  
  
 lu62_overlay_len  
 This value contains <strong>sizeof(</strong>struct **lu62_overlay)**–**sizeof(lu62_entry_len)**.  
  
 lu_name  
 LU name (EBCDIC type A).  
  
 lu_alias  
 LU alias (ASCII).  
  
 num_plus  
 Number of partner LUs.  
  
 fqlu_name  
 Fully qualified LU name (EBCDIC type A).  
  
 default_lu  
 For local LU group, an LU equal to the **default_lu** is used if none is specified. Legal values are AP_NO and AP_YES.  
  
 On Host Integration Server, there is no concept of a default local LU. Therefore, the **default_lu** flag, which is set to AP_YES for the node in IBM ES for OS/2 version 1.0, is set to AP_NO for Host Integration Server.  
  
 lu_local_addr  
 NAU address, 0–254.  
  
 lu_sess_lim  
 Configured session limit, 0–255.  
  
 max_tps  
 Maximum number of TPs, 1–255.  
  
 lu_type  
 Always LU type 6.2.  
  
 For each configured LU, a **plu_62_overlay** structure for the partner LU is provided as defined below.  
  
## Syntax  
  
```  
typedef struct plu62_overlay {  
    unsigned long  plu62_entry_len;  
    unsigned long  plu62_overlay_len;  
    unsigned char  plu_alias[8];  
    unsigned short num_modes;  
    unsigned char  plu_un_name[8];  
    unsigned char  fqplu_name[17];  
    unsigned char  reserv3;  
    unsigned char  plu_sess_lim;  
    unsigned char  dlc_name[8];  
    unsigned char  adapter_num;  
    unsigned char  dest_addr_len;  
    unsigned char  dest_addr[32];  
    unsigned int   par_sess_supp:1;  
    unsigned int   reserv4:7;  
    unsigned int   def_already_ver:1;  
    unsigned int   def_conv_sec:1;  
    unsigned int   def_sess_sec:1;  
    unsigned int   reserv5:5;  
    unsigned int   act_already_ver:1;  
    unsigned int   act_conv_sec:1;  
    unsigned int   reserv6:6;  
    unsigned int   implicit_part:1;  
    unsigned int   reserv7:7;  
} PLU62_OVERLAY;  
```  
  
## Members  
 plu62_entry_len  
 Size of this partner LU entry.  
  
 plu62_overlay_len  
 This value contains <strong>sizeof(</strong>struct **plu62_overlay)**–**sizeof(plu62_entry_len)**.  
  
 plu_alias  
 Partner LU alias (ASCII).  
  
 num_modes  
 Number of modes.  
  
 plu_un_name  
 Partner LU uninterpreted name (EBCDIC).  
  
 fqplu_name  
 Fully qualified partner LU name (EBCDIC type A).  
  
 reserv3  
 Reserved field set to zero.  
  
 plu_sess_lim  
 Partner LU session limit, 0–255.  
  
 dlc_name  
 DLC name (ASCII).  
  
 adapter_num  
 DLC adapter number.  
  
 dest_addr_len  
 Length of destination adapter address.  
  
 dest_addr  
 Destination adapter address.  
  
 par_sess_supp  
 Bit 15 of a bitfield specifying parallel sessions. Valid values are AP_NOT_SUPPORTED and AP_SUPPORTED.  
  
 reserv4  
 Bits 8–14 of a bitfield specifying a reserved field set to zero.  
  
 def_already_ver  
 Bit 7 of a bitfield specifying whether the configured already verified option is supported. Valid values are AP_NOT_SUPPORTED and AP_SUPPORTED.  
  
 def_conv_sec  
 Bit 6 of a bitfield specifying whether the configured conversation security option is supported. Valid values are AP_NOT_SUPPORTED and AP_SUPPORTED.  
  
 def_sess_sec  
 Bit 5 of a bitfield specifying whether the configured session security option is supported. Valid values are AP_NOT_SUPPORTED and AP_SUPPORTED.  
  
 reserv5  
 Bits 0–4 of a bitfield specifying a reserved field set to zero.  
  
 act_already_ver  
 Bit 15 of a bitfield specifying whether the active already verified option is supported. Valid values are AP_NOT_SUPPORTED and AP_SUPPORTED.  
  
 act_conv_sec  
 Bit 14 of a bitfield specifying whether the active conversation security option is supported. Valid values are AP_NOT_SUPPORTED and AP_SUPPORTED.  
  
 reserv6  
 Bits 8–13 of a bitfield specifying a reserved field set to zero.  
  
 implicit_part  
 Bit 7 of a bitfield specifying whether this is an implicit partner. Valid values are AP_NO and AP_YES.  
  
 For partner LU group, **implicit_part** indicates the partner LU group was configured as an implicit primary logical unit (PLU).  
  
 reserv7  
 Bits 0–6 of a bitfield specifying a reserved field set to zero.  
  
## Remarks  
 Host Integration Server returns information on all the configured LU 6.2s in the system, including the implicit PLU and all instances of implicit modes. IBM ES for OS/2 version 1.0 only returns information on those that are in use or have been in use.  
  
 For partner LU group, **implicit_part** indicates the partner LU group was configured as an implicit primary logical unit (PLU).  
  
 For mode group, **implicit_mode** bitfield returned in the **mode_overlay** structure indicates the mode group was configured as an implicit mode.