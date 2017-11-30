---
title: "Extracting LUWIDs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9cbfe30-4e47-4f40-8693-d1fd40435888
caps.latest.revision: 3
---
# Extracting LUWIDs
Both LUWIDs for a particular TP can be determined by issuing the [GET_TP_PROPERTIES](../HIS2010/get-tp-properties1.md) verb. The **GET_TP_PROPERTIES** verb returns the TP's unprotected LUWID in the **luw_id** field.  
  
 If the TP needs to access the protected LUWID, it must combine the **opext** member of the verb control block (VCB) with the value AP_EXTD_VCB using OR before issuing the verb. The protected LUWID will then be returned in the **prot_luw_id** field. If the **opext** field does not contain the AP_EXTD_VCB bit, the verb control block is presumed to end immediately before the **prot_luw_id** field.  
  
 The LUWID for a particular conversation can be determined by issuing a [GET_ATTRIBUTES](../HIS2010/get-attributes1.md) or [MC_GET_ATTRIBUTES](../HIS2010/mc-get-attributes1.md) verb on the conversation. These verbs are modified as follows:  
  
-   A new field, **luw_id**, is added in which the LUWID is returned. The LUWID returned is the protected one if the conversation was allocated with **synclevel** field of the [ALLOCATE](../HIS2010/allocate1.md) or [MC_ALLOCATE](../HIS2010/mc-allocate1.md) verb set to Sync Point (AP_SYNCPT); otherwise it is the unprotected one.  
  
-   Since the **luw_id** field cannot be incorporated within the existing verb control blocks, the TP must use a larger VCB structure. To indicate that the VCB is longer than usual, the **opext** field of the VCB must be combined with the value AP_EXTD_VCB using OR before calling APPC.  
  
-   The **sync_level** field of the **GET_ATTRIBUTES** or **MC_GET_ATTRIBUTES** verb can take an additional value, AP_SYNCPT, when the conversation was allocated with the **synclevel** field of the **ALLOCATE** or **MC_ALLOCATE** verb of Sync Point (AP_SYNCPT).