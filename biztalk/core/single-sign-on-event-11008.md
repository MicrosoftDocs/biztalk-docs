---
description: "Learn more about: Single Sign-On: Event 11008"
title: "Single Sign-On: Event 11008"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On: Event 11008
## Details  
  
| Field | Error Details|
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                 Enterprise Single Sign-On                                                                 |
| Product Version |                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                 |
|    Event ID     |                                                                           11008                                                                           |
|  Event Source   |                                                                          ENTSSO                                                                           |
|    Component    |                                                                            N/A                                                                            |
|  Symbolic Name  |                                                                   SSO_WARN_CHECK_GROUP                                                                    |
|  Message Text   | Check group membership failed.%r<br /><br /> Group Name: %1%r<br /><br /> Account Name: %2%r<br /><br /> Additional Data: %3%r<br /><br /> Error Code: %4 |
  
## Explanation  
 This is most likely caused by network issues, cross-domain use, or a mixed level of domain controllers (for example, if your system uses domain controllers from both [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]).  
  
## User Action  
 Check with your network administrator to see if there are any network issues, or if your system has any cross-domain use or mixed level of domain controllers.
