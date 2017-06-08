---
title: "Stop Application Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.application.stop.dialog"
ms.assetid: 2941db8a-24c6-4ebf-bf45-03827e9d9491
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Stop Application Dialog Box
Use the **Stop Application** dialog box to suspend all activation messages, unenlist orchestrations and send ports, disable receive locations, and control running artifact instances.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Stop**|Click to stop the application and execute selected tasks.|  
|**Options**|Click to expand the **Stop Application** dialog box or, if the dialog box is already expanded, to collapse it.|  
  
## Options Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Partial Stop - Allow running instances to continue**|Select to disable only receive locations. Receive locations will stop receiving inbound messages and submitting them to the Message Box.|  
|**Partial Stop - Suspend running instances**|Select to disable receive locations and to stop all orchestrations and send ports. Receive locations will stop receiving inbound messages and submitting them to the Message Box. Orchestration subscriptions will be disabled, and send port subscriptions will be removed.|  
|**Full Stop - Terminate instances**|Select to disable receive locations, unenlist orchestrations and send ports, and undeploy policies. Receive locations will stop receiving inbound messages and submitting them to the Message Box. Orchestration subscriptions will be disabled, and send port subscriptions will be removed. All policies (rules) will be removed from production.|  
  
## Referenced Applications Tab  
 Each check box represents an application that is referenced by the current one. If the check box next to an application name is selected, that application will stop when the current application stops.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**\<application name> Application**|Select the check box for each referenced application that you want to include when you stop the application.|  
  
## See Also  
 [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md)   
 [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)