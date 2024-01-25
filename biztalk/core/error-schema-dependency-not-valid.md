---
description: "Learn more about: Error - Schema Dependency Not Valid"
title: "Error - Schema Dependency Not Valid"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.schemaDependencyNotValid"
---
# Error - Schema Dependency Not Valid
**Error Code**  
  
 BEC2009  
  
 **Explanation**  
  
 All dependent schemas, such as those that are imported, included, or redefined in the current schema, must be added to this BizTalk project or exist in an assembly referenced by this project. Even schema **import**, **include**, and **redefine** directives that specify schemas on a remote Web site must be added to this BizTalk project.  
  
 **User Action**  
  
 Use the **Add Existing Item** command on the **File** menu and the shortcut menu for the Microsoft® BizTalk® Server project to add all schemas upon which this schema depends to the BizTalk project. You may need to download such schemas from a Web site to your local hard disk before adding them to the BizTalk project.
