---
title: "Rejecting Remotely Initiated Conversations1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd7e2524-c418-4c93-8300-48f4c7bf715c
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Rejecting Remotely Initiated Conversations
In an environment where a Sync Point Attach Manager is receiving all Attach messages as described above, it may be necessary for it to reject an Attach for a particular TP name, either because the TP name is not valid or because there is another problem with the received Attach message. To enable the application to generate the correct return code at the initiating TP, the [DEALLOCATE](../Topic/DEALLOCATE1.md) and [MC_DEALLOCATE](../Topic/MC_DEALLOCATE1.md)verbs are enhanced with new **deallocate_type** field values in the VCB that allow the application to specify the return code to be sent to the initiating TP. The new values for **deallocate_type** are:  
  
 AP_TP_NOT_AVAIL_RETRY  
  
 AP_TP_NOT_AVAIL_NO_RETRY  
  
 AP_TPN_NOT_RECOGNIZED  
  
 AP_PIP_DATA_NOT_ALLOWED  
  
 AP_PIP_DATA_INCORRECT