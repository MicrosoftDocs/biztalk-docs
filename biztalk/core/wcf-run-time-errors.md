---
description: "Learn more about: WCF Run-Time Errors"
title: "WCF Run-Time Errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# WCF Run-Time Errors
Information for diagnosing and resolving WCF run-time events.  
  
## WCF service host restarted
  
|     Field       |                                    Error Details                                   |
|-----------------|------------------------------------------------------------------------------------|
|  Product Name   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| Product Version |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    Event ID     |                                       0x1FB0                                       |
|  Event Source   |                                         0                                          |
|    Component    |                                         0                                          |
|  Symbolic Name  |                          BTS_I_WCF_SERVICE_HOST_RESTARTED                          |
|  Message Text   |                                         0                                          |
  
## Explanation  
 This message provides a way for the WCF adapter to write an “informational” event log entry (the provided APIs for adapters allow the creation of warnings or errors, not information).  
  
## User Action  
 If you see this informational event in the event log, it indicates that the auto-recovery has succeeded. No further action in regard to this message is necessary.
