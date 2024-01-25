---
description: "Learn more about: REOverride Guidelines"
title: "REOverride Guidelines1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# REOverride Guidelines
Use the following guidelines for when to use REOverride to set an RE programmatically:  
  
-   Avoid hard-coding RE names into applications. Instead, load RE names from a file or database.  
  
-   Ensure that applications are structured to handle failures when they attempt to set the RE.  
  
-   Structure your application code to use a list of RE names. This practice reduces errors caused by missing REs.  
  
-   Ensure that procedures for adding and configuring REs include a mechanism to update REs referenced in the application code.  
  
> [!NOTE]
>  Use REOverride to confirm that administrative and operational tasks do not interfere with application code that sets an RE. Specifically, review when and how REs are deactivated and deleted.  
  
 To implement RE selection by using REOverride, you must ensure that the TI component starts out with an associated RE instance even though the application will set the RE programmatically. The RE that is currently assigned to the component is used when an application does not explicitly set the RE.  
  
## See Also  
 [Specifying a Remote Environment Programmatically](../core/specifying-a-remote-environment-programmatically1.md)
