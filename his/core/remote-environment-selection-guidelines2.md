---
title: "Remote Environment Selection Guidelines2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bdfcf97-e218-41a6-a81a-8d4cf85fb0a4
caps.latest.revision: 3
---
# Remote Environment Selection Guidelines
Consider these guidelines when you are using the `SelectionHint` property to specify a remote environment (RE) programmatically:  
  
-   Avoid hard-coding RE names into applications. Instead, load RE names from a file or database.  
  
-   Ensure that applications are structured to handle failures when they are attempting to set the `SelectionHint` property.  
  
-   Ensure that procedures for adding and configuring REs include a mechanism to update REs referenced in the application code.  
  
-   Confirm that administrative and operational tasks do not interfere with application code that uses the RE selection. Specifically, review when and how REs are deactivated and deleted.  
  
## See Also  
 [Remote Environment Selection with the SelectionHint Property](../core/remote-environment-selection-with-the-selectionhint-property1.md)