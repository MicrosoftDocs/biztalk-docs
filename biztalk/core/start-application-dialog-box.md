---
title: "Start Application Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.application.start.dialog"
ms.assetid: 4276b81e-5d2e-4e59-a5a9-1401f61d9ce3
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Start Application Dialog Box
Use the **Start Application** dialog box to start all dependent artifacts and applications in one transaction.  
  
 When you open this dialog box, it is displayed in a collapsed form (without the **Options** or **Referenced Applications** tab visible) if all applications that the current application references are already running. If any of the referenced applications has not already been started when you open this dialog box to start the current application, the dialog box will open with the **Details** portion of the dialog box expanded so that you can see the referenced applications that will also be started.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Start**|Click to start the application and the selected artifacts and referenced applications.|  
|**Options**|Click to expand the **Start Application** dialog box and display the **Options** and **Referenced Applications** tabs.|  
  
## Options Tab  
 Each check box represents an application artifact that will start automatically when you start the application unless you specify otherwise. All check boxes are selected by default.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Application artifacts - Start all orchestrations**|Select this check box to start all orchestrations when you start the application.|  
|**Application artifacts - Start all send ports**|Select this check box to start all send ports when you start the application.|  
|**Application artifacts - Start all send port groups**|Select this check box to include all send port groups when you start the application.|  
|**Application artifacts - Enable all receive locations**|Select this check box to enable receive locations when you start the application. Enabled receive locations can accept inbound messages and submit them to the Message Box.|  
|**Application artifacts - Start all associated host instances**|Select this check box to enable host instances to begin processing documents when you start the application.|  
|**Deploy all policies**|Select this check box to deploy all policies (rules) when you start the application.|  
|**Instances - Resume suspended instances**|Select this check box to resume suspended orchestration instances when you start the application.|  
  
## Referenced Applications Tab  
 Each check box represents an application that is referenced by the current one. If the check box next to an application name is selected, that application will start when the current application starts.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**\<application name> Application**|Select the check box for each referenced application that you want to include when you start the application.|  
  
## See Also  
 [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md)   
 [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)   
 [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md)