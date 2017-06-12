---
title: "Move to Application Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.movetoapplication"
ms.assetid: a12e2b40-61df-4baf-b5e1-55db51828e89
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Move to Application Dialog Box
Use the **Move to Application** dialog box to move artifacts from the default application in the Administrative Console to separate applications. During an upgrade to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], artifacts that existed in earlier versions of BizTalk Server are placed into the default application. After the upgrade, the **Move to Application** dialog box enables you to distribute these artifacts among different applications that reflect your business topology. You can also use the **Move to Application** dialog box to move artifacts between applications at any time.  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Destination application**|From the drop-down list, select the application to which you want to move the artifacts you selected in the Administration Console details pane.|  
|**Moving Artifacts - Name**|Displays a list of artifacts that will be moved. The list contains all artifacts that were selected when you opened the Move to Application dialog box and any dependent artifacts whose relationship with other artifacts in the list would be violated by the move.|  
|**Moving Artifacts - Dependency Details**|Summarizes reasons why the artifact will be moved. Possible reasons include:<br /><br /> -   **(Artifact1 is) Dependent On \<Artifact2>**. Artifact1 and Artifact2 must share the same application, or Artifact2 must be in an application referenced by the application that contains Artifact1. You can avoid moving Artifact1 when moving Artifact2 by adding a reference from the destination application to the application that contains Artifact1.<br />-   **(Artifact1 is) Required By \<Artifact2>**. Artifact1 and Artifact2 must share the same application, or Artifact1 must be in an application referenced by the application that contains Artifact2. You can avoid moving Artifact1 when moving Artifact2 by adding a reference from the application that contains Artifact1 to the destination application.<br />-   **(Artifact1 is) [Packaged In/Contains/Assembled with] \<Artifact2>**. Artifact1 and Artifact2, though displayed separately in the Management Console, are actually part of a single object and must be kept in the same application. They will always move together.<br />-   **(Artifact1 is) Selected by User**. The artifact is one that you selected to move.|