---
title: "Managing Role Links | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8860e11-3d2c-450f-a7d2-cc116478999c
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manage Role Links

## Overview
This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to manage role links in a BizTalk application. A role link defines the relationship between parties involved in a business transaction and specifies the message and port types used in the interaction in both directions. For background information on role links, see [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md).  

## Added to application  
 Role links are built in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies. You cannot add role links to an application individually; a role link is added to an application as follows:  
  
- When you add a BizTalk assembly containing a role link to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
- When you import an .msi file into an application that includes a BizTalk assembly containing a role link, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).  
  
- When a developer deploys into an application an assembly containing a role link from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  

## Deploy to production  
 The BizTalk application developer creates role links to implement communications between two or more parties involved in a business transaction, such as your organization and a supplier. The developer does not necessarily specify the parties that are involved in the transaction, only their roles. To deploy an application that includes a role link to a production environment and enable actual communication between the parties, the following configuration must be performed, as described in this section:  
  
- If it wasn't done during the development process, a party must be assigned to each role defined in the role link. This is called "enlisting" a party for a role. You can later unenlist the party if you no longer want the party to have the assigned role.  
  
- The logical ports for each party defined within the role link must be bound to physical ports on the BizTalk host instances that will host the application.  
  
  For more information about developing role links, see [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md).  
  
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
## Next step
  
-   [How to Enlist or Unenlist a Party for a Role](../core/how-to-enlist-or-unenlist-a-party-for-a-role.md)