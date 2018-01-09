---
title: "Management Services Information2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37aee1be-febb-484a-b4cd-1063015dd252
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Management Services Information
Information on management services is provided in the **ms_info_sect** structure as defined below.  
  
## Syntax  
  
```  
typedef struct ms_info_sect {  
    unsigned long  ms_init_sect_len;  
    unsigned char  held_mds_mu_alerts;  
    unsigned char  held_nmvt_alerts;  
    unsigned short num_fps;  
    unsigned short total_fps;  
    unsigned short num_ms_appls;  
    unsigned short total_ms_appls;  
    unsigned short num_act_trans;  
    unsigned short total_act_trans;  
} MS_INFO_SECT;  
```  
  
## Members  
 ms_init_sect_len  
 The length of the initial MS information section, including this parameter, up to the first MS focal point group. The length does not include any previous information sections.  
  
 held_mds_mu_alerts  
 The number of management service MDS alerts being held that will be sent to the management service alert focal point (FP) when one becomes available.  
  
 held_nmvt_alerts  
 The number of management service NMVT alerts being held that will be sent to the management service alert focal point (FP) when one becomes available.  
  
 num_fps  
 The number of management service focal points (MS FPs) for which the information listed under MS Focal Point Group is returned. This is the number of times the information group is repeated.  
  
 total_fps  
 The total number of management service focal points for which APPC has information. This number is the same as the number returned in the **num_fps** member except when APPC has more information about management service focal points than it can place in the supplied buffer, in which case this number is larger.  
  
 num_ms_appls  
 The number of registered MS applications for which the information listed under Registered MS Application Group is returned. This is the number of times the information group is repeated.  
  
 total_ms_appls  
 The total number of registered MS applications for which APPC has information. This number is the same as the number returned in the **num_ms_appls** member except when APPC has more information about registered MS applications than it can place in the supplied buffer, in which case this number is larger.  
  
 num_act_trans  
 The number of MS active transactions for which the information listed under MS Active Transaction Group is returned. This is the number of times the information group is repeated.  
  
 total_act_trans  
 The number or MS active transactions for which APPC has information. This number is the same as the number returned in the **num_act_trans** member except when APPC has more information about registered MS active transactions than it can place in the supplied buffer, in which case this number is larger.  
  
 For each local and remote management service focal point group, an **ms_fp_overlay** structure for the focal point group is provided as defined below.  
  
## Syntax  
  
```  
typedef struct ms_fp_overlay {  
    unsigned long  ms_fp_entry_len;  
    unsigned char  ms_appl_name[8];  
    unsigned char  ms_category[4];  
    unsigned char  fp_fq_cp_name[17];  
    unsigned char  bkup_appl_name[8];  
    unsigned char  bkup_fp_fq_cp_name[17];  
    unsigned char  reserv1;  
    unsigned char  fp_type;  
    unsigned char  fp_status;  
    unsigned char  fp_routing;  
} MS_FP_OVERLAY;  
```  
  
## Members  
 ms_fp_entry_len  
 Size of this management service focal point information entry.  
  
 ms_appl_name  
 The management service application name of the current active focal point (EBCDIC).  
  
 ms_category  
 The management service category.  
  
 fp_fq_cp_name  
 The fully qualified control point name of the node on which the current (active) management service focal point is located (EBCDIC). If the local node has no focal point, a value of all EBCDIC space characters (0x40) is returned.  
  
 bkup_appl_name  
 The management service application name of the backup focal point, if one is known (EBCDIC).  
  
 bkup_fp_fq_cp_name  
 The fully qualified control point name of the node on which the backup management service focal point is located, if one is known (EBCDIC). If the local node has no backup focal point, a value of all EBCDIC space characters (0x40) is returned.  
  
 fp_type  
 The type of the focal point for the local management service entry point node. The focal point type depends on how the focal point-end point relationship was established, and on whether the local node is configured as an NN, EN, or LEN node (an EN without CP-CP session support). The type can be one of the following:  
  
 AP_EXPLICIT_PRIMARY_FP  
 The current focal point type is explicit primary.  
  
 AP_BACKUP_FP  
 The current focal point type is back up.  
  
 AP_DEFAULT_PRIMARY_FP  
 The current focal point type is default primary.  
  
 AP_DOMAIN_FP  
 The current focal point type is domain.  
  
 AP_HOST_FP  
 The current focal point type is host.  
  
 AP_NO_FP  
 Currently the local node has no focal point.  
  
 fp_status  
 The status of the management service focal point. The status can be one of the following:  
  
 AP_NOT_ACTIVE  
 The focal point has been acquired, but has since become unavailable.  
  
 AP_ACTIVE  
 The remote focal point has been acquired and is available.  
  
 AP_PENDING  
 A request has been sent to a remote primary or backup focal point to acquire that FP, and its reply has not yet been received.  
  
 AP_NEVER_ACTIVE  
 The focal point has never been acquired, but one or more registered management service applications have requested focal point information.  
  
 fp_routing  
 The routing used to send unsolicited requests to the management service focal point when the local node is an EN. Note that requests from an NN are always sent directly to the focal point.  
  
 The routing can be one of the following:  
  
 AP_DEFAULT  
 Unsolicited management service requests destined for the focal point are sent from the EN to its serving NN for forwarding to the focal point.  
  
 AP_DIRECT  
 Unsolicited management service requests destined for the focal point are sent directly to the focal point.  
  
## Remarks  
 When a program registers a management service application name, it can request focal point information. When APPC acquires the focal point, it passes the program the focal point information, which includes the type of routing to use to send unsolicited management service requests to the focal point.