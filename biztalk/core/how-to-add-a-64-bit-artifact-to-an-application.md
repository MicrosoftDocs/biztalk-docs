---
description: "Learn more about: How to Add a 64-Bit Artifact to an Application"
title: "How to Add a 64-Bit Artifact to an Application"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Add a 64-Bit Artifact to an Application
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes support for 64-bit applications. This means that you can add 64-bit artifacts to a BizTalk application in the same manner as 32-bit artifacts; however, you may encounter the following issues when installing the following 64-bit artifacts on a 32-bit computer:  
  
- **Virtual directory from a Web server that is running a 64-bit worker process.** The virtual directory will install on a 32-bit computer, but it may not function correctly. A mismatch will be logged.  
  
- **Unmanaged COM or Managed COM+ components marked as 64 bit.** These components will not install on a 32-bit computer.  
  
- **64-bit scripts saved as .exe files.** This type of script may not function correctly.  
  
  For general instructions on adding artifacts, see [How to Create or Add an Artifact](../core/how-to-create-or-add-an-artifact.md). For instructions on adding specific artifact types, see [Managing Artifacts](../core/managing-artifacts.md).  
  
## See Also  
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)   
 [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md)
