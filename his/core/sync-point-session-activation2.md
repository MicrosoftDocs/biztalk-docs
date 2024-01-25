---
description: "Learn more about: Sync Point Session Activation"
title: "Sync Point Session Activation2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Sync Point Session Activation
If Host Integration Server is to support Sync Point conversations, this must be specified at session activation time. The configuration of Host Integration Server is modified to allow the system administrator to specify which (if any) local LUs will be used for Sync Point conversations.  
  
 The **Local LU Configuration** property page in Host Integration Server contains a new check box. When checked, it indicates that the local LU can participate in Sync Point sessions. Host Integration Server uses this option to determine the parameters it sends on BIND requests and responses.  
  
 When Host Integration Server initiates an LU 6.2 session on an LU designated as supporting Sync Point, it sets the synchronization level on BIND requests to indicate that the session can support Sync Point and Backout. If the partner LU also supports Sync Point and Backout, the session is available for conversations requiring Sync Point support. If the partner LU does not support Sync Point, the session will not be used for Sync Point conversations.  
  
 Similarly, if the local LU is configured for Sync Point and the partner LU's BIND request indicates that it supports Sync Point, Host Integration Server sends BIND responses specifying that Sync Point is supported. In this case, the session can be used for Sync Point conversations.
