---
title: "Policy Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.policy.properties"
ms.assetid: b44d2456-7079-4a08-89f5-a79029178ee6
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Policy Properties Dialog Box
Use the **Policy Properties** window to view the rule sets that have been added to the application and to configure tracking options. Policy properties are defined in the Microsoft Business Rules Composer.  
  
## General Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Displays the policy name.|  
|**Version**|Displays the policy version.|  
|**State**|Indicates whether the policy is unpublished (in process of development), published (protected from further change) or deployed (placed into production).|  
|**Description**|Displays notes about the policy. This description is specified in the rule composer or through the rules engine.|  
  
## Tracking Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Track - Fact activity**|Select this check box to track the instance data on which the policy operates.|  
|**Track - Condition evaluation**|Select this check box to track the true/false results of conditions in the selected policy.|  
|**Track - Rule firings**|Select this check box to track the actions triggered as a result of the policy.|  
|**Track - Agenda updates**|Select this check box to track updates to the agenda. The agenda contains a list of actions that are "true" and need to fire.|  
  
> [!NOTE]
>  You can view tracked rules and policies during runtime using the queries on the Group Hub page.  
  
## See Also  
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)