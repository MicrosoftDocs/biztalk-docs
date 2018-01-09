---
title: "Starting Local Sync Point TPs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b16cb478-a9e5-4b2e-b8fa-d9f5af5b3e7b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Starting Local Sync Point TPs
Local TPs are created by issuing the [TP_STARTED](./tp-started2.md) verb to Host Integration Server. The **TP_STARTED** verb has been modified by adding the new verb control block (VCB) member **syncpoint_rqd** to allow a TP to specify that it requires Sync Point services.  
  
 By setting **syncpoint_rqd** to AP_YES, a TP indicates that it requires Sync Point services from Host Integration Server. A value of AP_NO (the default) indicates that Sync Point services are not required.  
  
 Since this member cannot be incorporated within the existing **TP_STARTED** VCB, the TP must use a larger VCB structure. To indicate that the VCB is longer than usual, the **opext** member of the VCB must be combined using OR with the value AP_EXTD_VCB before calling APPC.  
  
 Conversations started by TPs requiring Sync Point support will be routed only by the Host Integration Server software running on the same computer. They will not be routed to other LAN-attached servers.