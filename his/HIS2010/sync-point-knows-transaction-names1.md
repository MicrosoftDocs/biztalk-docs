---
title: "Sync Point Knows Transaction Names1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 415cc642-52f4-4a9b-af78-ac97f2665d0a
caps.latest.revision: 3
---
# Sync Point Knows Transaction Names
A Sync Point implementation that knows the names of all the transactions that can be supported (for example, through configuration of the gateway) may accept incoming Sync Point conversations by issuing a [RECEIVE_ALLOCATE](../HIS2010/receive-allocate2.md) verb specifying the name of the transaction and indicating that it is willing to accept Sync Point conversations.  
  
 The **RECEIVE_ALLOCATE** verb was modified to allow a TP to specify that it can accept Sync Point conversations by adding a new **syncpoint_rqd** field to the VCB. When this field is set to AP_YES it indicates that the transaction program can accept Sync Point conversations from Host Integration Server. When this field is set to AP_NO (the default), it indicates that Sync Point conversations are not supported.