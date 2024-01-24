---
description: "Learn more about: Rejecting Remotely Initiated Conversations"
title: "Rejecting Remotely Initiated Conversations1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Rejecting Remotely Initiated Conversations
In an environment where a Sync Point Attach Manager is receiving all Attach messages as described above, it may be necessary for it to reject an Attach for a particular TP name, either because the TP name is not valid or because there is another problem with the received Attach message. To enable the application to generate the correct return code at the initiating TP, the [DEALLOCATE](./deallocate2.md) and [MC_DEALLOCATE](./mc-deallocate2.md)verbs are enhanced with new **deallocate_type** field values in the VCB that allow the application to specify the return code to be sent to the initiating TP. The new values for **deallocate_type** are:  
  
 AP_TP_NOT_AVAIL_RETRY  
  
 AP_TP_NOT_AVAIL_NO_RETRY  
  
 AP_TPN_NOT_RECOGNIZED  
  
 AP_PIP_DATA_NOT_ALLOWED  
  
 AP_PIP_DATA_INCORRECT
