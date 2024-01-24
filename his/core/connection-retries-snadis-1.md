---
description: "Learn more about: Connection Retries (SNADIS)"
title: "Connection Retries (SNADIS)1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Connection Retries (SNADIS)
If an initially active or operator-started connection is closed because of an outage, the node periodically tries to reopen the connection. This can be stopped by manually deactivating the connection. This retry mechanism is also used when the node attempts to open a connection but the SNALink software has not yet been started. On-demand connections are not retried automatically by the node, but will be retried if the user attempts to reactivate a session using the connection.  
  
 Note that this connection retry timer is totally separate from the timers specified on the [Open(LINK) Request](./open-link-request1.md).
