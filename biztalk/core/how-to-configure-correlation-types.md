---
description: "Learn more about: How to Configure Correlation Types"
title: "How to Configure Correlation Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deleting, correlation types"
  - "correlation types, configuring"
  - "correlation types, deleting"
  - "configuring, correlation types"
ms.assetid: cfae4d2e-ec79-45c8-93b3-799dc5e0576e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Correlation Types
You use the **Correlation Properties** dialog box to add or remove properties from a correlation type. The correlation type lists the properties in a correlation set which are used by Send and Receive activities to make sure that incoming messages are properly correlated with the right instances of an orchestration at run time.  
  
 There are two panes in the dialog box, each containing a list of properties. The left pane, "Available Properties", contains a tree view of all of the properties that are defined in your project or referenced by it. The properties that appear by default are system properties, defined by BizTalk Server, but you can also define your own properties in a property schema. For more information about creating property schemas, see [Property Schemas](../core/property-schemas.md).  
  
> [!NOTE]
>  Schema properties must be promoted before they can be used in a correlation type. For more information, see [Promoting Properties](../core/promoting-properties.md).  
  
### To add and configure a correlation type  
  
-   In the Orchestration View window, right-click **Correlation Types** and then click **New Correlation Type**.  
  
     The **Correlation Properties** dialog box comes up. Add properties that you want to include in your correlation type.  
  
    > [!NOTE]
    >  If you access the **Correlation Properties** dialog box directly from a correlation set, a correlation type for the correlation set is created if one does not already exist. Your changes will be saved to the new correlation type, and the correlation set will be configured to use the new correlation type. If a correlation type already existed for the correlation set and you make changes, the correlation type will be modified.  
  
### To remove a correlation type  
  
-   In the Orchestration View window, right-click the correlation type you want to remove and then click **Delete**.
