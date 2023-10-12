---
description: "Learn more about: Remote Environment Selection Guidelines"
title: "Remote Environment Selection Guidelines1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Remote Environment Selection Guidelines
Consider these guidelines when you are using the `SelectionHint` property to specify a remote environment (RE) programmatically:  
  
-   Avoid hard-coding RE names into applications. Instead, load RE names from a file or database.  
  
-   Ensure that applications are structured to handle failures when they are attempting to set the `SelectionHint` property.  
  
-   Ensure that procedures for adding and configuring REs include a mechanism to update REs referenced in the application code.  
  
-   Confirm that administrative and operational tasks do not interfere with application code that uses the RE selection. Specifically, review when and how REs are deactivated and deleted.  
  
## See Also  
 [Remote Environment Selection with the SelectionHint Property](../core/remote-environment-selection-with-the-selectionhint-property2.md)
