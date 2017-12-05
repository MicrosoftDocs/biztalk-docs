---
title: "Connection Retries (SNADIS)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f05c1d2-0cee-404f-893f-2b6d1fcee7c6
caps.latest.revision: 3
---
# Connection Retries (SNADIS)
If an initially active or operator-started connection is closed because of an outage, the node periodically tries to reopen the connection. This can be stopped by manually deactivating the connection. This retry mechanism is also used when the node attempts to open a connection but the SNALink software has not yet been started. On-demand connections are not retried automatically by the node, but will be retried if the user attempts to reactivate a session using the connection.  
  
 Note that this connection retry timer is totally separate from the timers specified on the [Open(LINK) Request](../HIS2010/open-link-request2.md).