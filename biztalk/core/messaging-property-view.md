---
description: "Learn more about: Messaging Property View"
title: "Messaging Property View | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking Profile Editor, message schemas"
  - "message schemas, properties"
  - "Messaging Property view [Tracking Profile Editor]"
  - "Tracking Profile Editor, Messaging Property view"
  - "message schemas, XML messages"
ms.assetid: 80d040e9-d58b-41d1-b26d-19aff4d3126b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Messaging Property View
The Messaging Property view displays the schema of the XML message associated with the property. The view is available from the shortcut menu for some of the shapes in the Orchestration Schedule view.  
  
## Working with messaging properties  
 You select your Messaging Property view by clicking the **Select Event Source** button and clicking the **Select Message Property** menu item. You then choose a message property from which to select a schema. Once you select the schema, you can drag elements from this schema to the data item folders of the activity, thus indicating that you want to extract that particular data from specific XPath expressions inside the message at this action.  
  
 You can open message property views from the Orchestration Schedule view by right-clicking a shape that contains a message payload. This will open a context menu from which you can click the Message Payload menu item to retrieve a list of payloads associated with the shape.  
  
 The list of available message properties can be extensive. If you know part of the name of the orchestration for which you are searching, you can type it in the **In String** text box and click the **Search** button. This will select only those message properties that contain the partial string you have entered.  
  
## See Also  
 [What Is the Source Event View?](../core/what-is-the-source-event-view.md)   
 [Tracking Profile Editor](../core/tracking-profile-editor.md)
