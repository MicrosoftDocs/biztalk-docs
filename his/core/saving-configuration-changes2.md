---
description: "Learn more about: Saving Configuration Changes"
title: "Saving Configuration Changes2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Saving Configuration Changes
If the SNA Manager is opened in the domain, it will attempt to obtain an exclusive lock on the configuration file when it is opened (unless opened in read-only mode). It is recommended that you do not run SNA Manager until all servers in the domain have been upgraded to Host Integration Server.  
  
 SNA Manager will lock the configuration file when a configuration change is initiated. When the change is completed and the configuration file is saved, then the configuration file lock will be released. The status bar will display **OUT OF DATE** on other servers in the domain. To refresh the status on the out-of-date servers, SNA Manager must be closed and reopened.
