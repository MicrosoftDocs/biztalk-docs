---
description: "Learn more about: TN3270 and Single Sign-On"
title: "TN3270 and Single Sign-On1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TN3270 and Single Sign-On
The TN3270 service does not work with Single Sign-On. You should not enable the TN3270 service to run under a user account for which you have a Single Sign-On mapping. If you access the host through the TN3270 service by typing **MS$SAME** for your logon, you will get the user ID and password of the user under which the TN3270 service is running (for example, SNAUSER). If you use an Administrator-level account and change the password, SNA services will fail to start after the password change.  
  
## See Also  
 [TN3270](../core/tn32702.md)
