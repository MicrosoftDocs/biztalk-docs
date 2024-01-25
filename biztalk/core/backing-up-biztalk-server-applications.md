---
description: "Learn more about: Backing Up BizTalk Server Applications"
title: "Backing Up BizTalk Server Applications"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Backing Up BizTalk Server Applications
To ensure that you can recover your BizTalk Server system after a hardware failure, it is important to have good backups. As a part of keeping backups, it is a good idea to export your BizTalk applications to a remote server and to back up these applications.  
  
 Later, when you restore the BizTalk Server databases and reinstall BizTalk Server, you can import these applications. For more information about how to export and import applications, see [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md).  
  
 For all BizTalk applications deployed on the computer, you should export the .msi files and save them in your backup location (on a different server). The .msi files enable you to reinstall the resources required by BizTalk Server after you recover the destination computer. You should ensure that the .msi files include all of the required resources, and that you specify the actions to be performed on the .msi installation for these resources. If your BizTalk application depends on any user assemblies or other DLLs that are not included in the .msi files, you must back up them up separately.  
  
 The application export process is the same for content-based routing scenarios as well as scenarios that have orchestrations. You should repeat this process whenever you change the BizTalk applications. For more information, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
## See Also  
 [Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md)
