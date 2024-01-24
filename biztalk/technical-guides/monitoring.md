---
description: "Learn more about: Monitoring"
title: "Monitoring"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Monitoring
By default, all BizTalk Server monitoring and tasks use the default action account when there is no specific Run As Account defined for the target in the Run As Profile of the BizTalk Server Monitoring Account. To configure a Run As Account with the minimum set of permissions that are required for BizTalk Server monitoring purposes, the following permissions are required:  
  
-   The account must be a member of the monitored computer’s built-in Administrators group and Performance Monitors Users group.  
  
-   The account must be a member of the SysAdmin role within the SQL instance or instances hosting the databases and jobs for the BizTalk group that is being monitored.  
  
-   For BizTalk Server monitoring purposes, the account must be a part of BizTalk Operators group.  
  
-   For running tasks through SCOM console, the account must be a part of BizTalk Application Users group.  
  
-   For performing administrative tasks, the account must be a part of BizTalk Administrator group.
