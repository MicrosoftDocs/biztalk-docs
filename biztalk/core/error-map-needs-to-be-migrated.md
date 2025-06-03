---
description: "Learn more about: Error - Map Needs to be Migrated"
title: "Error - Map Needs to be Migrated"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: upgrade-and-migration-article
f1_keywords: 
  - "bts10.map.error.mapNeedsMigrating"
---
# Error - Map Needs to be Migrated
**Error Code**  
  
 btm1064  
  
 **Explanation**  
  
 The map cannot be compiled because it was created using a previous version of BizTalk Mapper. You must migrate such maps to this version of BizTalk Mapper before they can be compiled.  
  
 **User Action**  
  
 Migrate the map to the current version of BizTalk Mapper by changing its file extension from "xml" to "btm", adding it to the relevant Microsoft BizTalk Server project. Use the **Add Existing Item** command available on the **File** menu and on the shortcut menu for the BizTalk project in Solution Explorer, and then open the map by double-clicking it in Solution Explorer. Because you have reached this topic, you have probably already performed the first two steps. Simply opening the map in the current version of BizTalk Mapper will perform an on-the-fly migration of the map.
