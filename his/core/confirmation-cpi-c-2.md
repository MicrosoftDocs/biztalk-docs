---
title: "Confirmation (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 503e0397-214b-4f9b-8886-7a204a3f46fd
caps.latest.revision: 3
---
# Confirmation (CPI-C)
The following table summarizes state changes that occur under the following conditions:  
  
-   The return_code parameter is CM_OK.  
  
-   The *data_received* parameter is set to CM_DATA_RECEIVED, CM_COMPLETE_DATA_RECEIVED, or CM_NO_DATA_RECEIVED.  
  
-   The *status_received* parameter indicates a change to a CONFIRM state.  
  
    |*status_received*|New state|  
    |------------------------|---------------|  
    |CM_CONFIRM_DEALLOC_RECEIVED|CONFIRM_DEALLOCATE|  
    |CM_CONFIRM_SEND_RECEIVED|CONFIRM_SEND|  
    |CM_CONFIRM_RECEIVED|CONFIRM|