---
title: "SNA Global Information2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8bd85866-c2b2-4274-b7a6-3dd329ab4661
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# SNA Global Information
SNA global information is defined or returned as described here.  
  
## Defined by IBM ES for OS/2 version 1.0  
 Information on SNA global information is provided in the **sna_global_info_sect** structure as defined below.  
  
```  
typedef struct sna_global_info_sect {  
    unsigned char version;  
    unsigned char release;  
    unsigned char net_name[8];  
    unsigned char pu_name[8];  
    unsigned char node_id[4];  
    type_product_set_id product_set_id;  
    unsigned char alias_cp_name[8];  
    unsigned char node_type;  
    unsigned char cp_nau_addr;  
    unsigned char corr_serv_disk;  
    unsigned char reserved;  
    unsigned char appc_version;  
    unsigned char appc_release;  
    unsigned char appc_fixlevel;  
} SNA_GLOBAL_INFO_SECT;  
```  
  
## Members  
 version  
 Communications Manager Extended Edition version number.  
  
 release  
 Communications Manager Extended Edition release number.  
  
 net_name  
 Network name, first part of fully qualified control program (CP) name, in EBCDIC (type A).  
  
 pu_name  
 PU name, second part of fully qualified CP name, in EBCDIC (type A).  
  
 node_id  
 4-byte hexadecimal exchange identifier.  
  
 product_set_id  
 Computer product data.  
  
 alias_cp_name  
 Node name (local name for CP) in ASCII.  
  
 node_type  
 AP_NN, AP_EN, or AP_LEN.  
  
 cp_nau_addr  
 CP NAU address where 0 means not used (an independent LU). Other legal values are 1 to 254.  
  
 corr_serv_disk  
 Last four digits of corrective service disk number.  
  
 reserved  
 Reserved field.  
  
 appc_version  
 APPC version number.  
  
 appc_release  
 APPC release number.  
  
 appc_fixlevel  
 APPC patch number.  
  
## Returned by Host Integration Server  
 Information on SNA global information is provided in the **sna_global_info_sect** structure defined below.  
  
```  
typedef struct sna_global_info_sect {  
    unsigned char version;  
    unsigned char release;  
    unsigned char net_name[8];  
    unsigned char pu_name[8];  
    unsigned char node_id[4];  
    type_product_set_id product_set_id;  
    unsigned char alias_cp_name[8];  
    unsigned char node_type;  
    unsigned char cp_nau_addr;  
    unsigned char corr_serv_disk;  
    unsigned char reserved;  
    unsigned char appc_version;  
    unsigned char appc_release;  
    unsigned char appc_fixlevel;  
} SNA_GLOBAL_INFO_SECT;  
```  
  
## Members  
 version  
 Major operating system version number.  
  
 release  
 Minor operating system version number.  
  
 net_name  
 Node network name in EBCDIC (type A).  
  
 pu_name  
 PU name in EBCDIC (type A) associated with connection.  
  
 node_id  
 Node identifier to send.  
  
 product_set_id  
 Set to EBCDIC zeros.  
  
 alias_cp_name  
 Node name, local name for the control program (CP), in ASCII.  
  
 node_type  
 Set to AP_LEN.  
  
 cp_nau_addr  
 CP NAU address where 0 means not used (an independent LU). Other legal values are 1 to 254.  
  
 corr_serv_disk  
 Reserved field set to zero.  
  
 reserved  
 Reserved field set to zero.  
  
 appc_version  
 Host Integration Server major version number.  
  
 appc_release  
 Host Integration Server minor version number.  
  
 appc_fixlevel  
 Host Integration Server patch number.  
  
## Remarks  
 Host Integration Server returns **version** and **release** as the major and minor operating system version numbers from **GetVersion**. Because Host Integration Server has no information on the computer type, serial number, and manufacturer, **product_set_id** is set to EBCDIC zeros.  
  
 Host Integration Server does not support APPN node types, so the node type is returned as 1 (an AP_LEN node), and not 2 or 3 (AP_NN or AP_EN nodes), as defined by IBM ES for OS/2 version 1.0.