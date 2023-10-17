---
description: "Learn more about: Host Integration Server and WMI on a Backup Server"
title: "Host Integration Server and WMI on a Backup Server1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Host Integration Server and WMI on a Backup Server
There are some restrictions on using Windows Management Instrumentation (WMI) and Host Integration Server regarding connections to backup servers. The Snabase works to synchronize the information in the COM.CFG configuration file on the primary server across all backup servers. Each backup server has a local copy of the COM.CFG file from this synchronization process. WMI has a limitation that it will not attempt to read the local backup server's copy of COM.CFG if the primary server is alive. This request will always be forwarded to the primary server.  
  
 A client that connects to a WMI provider running on a backup server cannot retrieve any information or make configuration changes. This is a limitation of DCOM which does not permit impersonation outside the local computer. When a client on one computer connects to a WMISNA provider on another computer that is a backup server, the client is using DCOM to connect to the backup Host Integration Server computer. When the WMI provider on the backup server tries to access the COM.CFG file from the primary server, this is not allowed by DCOM because the application is trying to impersonate the user across the computer boundary.  
  
 You can work around this limitation on Windows using delegation.  
  
 The limitation against accessing a remote COM.CFG file does not apply when the primary server is down. In this case the server will fail-over to a backup and use replicated copies.
