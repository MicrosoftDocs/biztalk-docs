---
description: "Learn more about: Context Property View"
title: "Context Property View | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking Profile Editor, message schemas"
  - "Context Property view [Tracking Profile Editor]"
  - "Tracking Profile Editor, Context Property view"
  - "message schemas, XML messages"
ms.assetid: 17a21b86-995c-4dc2-9a3c-1309837d0b9b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Context Property View
The Context Property view displays the schema of the XML message associated with the property. The view is available from the shortcut menu for some of the shapes in the Orchestration Schedule view.  
  
## Working with the Context Property view  
 You select your Context Property view by clicking the **Select Event Source** button and clicking the **Select Context Property** menu item. You then choose a context property from the list of known context properties to load the schema for that property. Once you select the property, you can drag elements from the associated schema to the data item folders of the activity, thus indicating you want to extract that data from specific XPath expression inside the message at this action.  
  
 You can open context property views from the orchestration schedule view by right-clicking a shape that contains a context property. This will open a context menu from which you can click the **Context Property Schema** menu item to retrieve a list of context properties associated with the shape.  
  
 The list of available context properties can be extensive. If you know part of the name of the property for which you are searching, you can type it in the **In String** text box and click the **Search** button. This will select only those properties that contain the partial string you have entered.  
  
> [!NOTE]
>  When you choose to map from the Context Properties view, the list of potential property schemas is a complete list of every property schema configured in your BizTalk Server installation.  You must aware that the schemas presented are not sensitive to which features in BizTalk Server are used by the running process on which you are working. For example, you can select a schema for SOAP properties from the list of schemas offered when mapping from Context Properties, but the running process itself may not use SOAP. Any BAM activity item mapped from an unused property results in null or empty data being captured by BAM.  
  
## See Also  
 [What Is the Source Event View?](../core/what-is-the-source-event-view.md)   
 [Tracking Profile Editor](../core/tracking-profile-editor.md)
