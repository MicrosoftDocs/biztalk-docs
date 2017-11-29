---
title: "How to Create and Modify an Adapter Group | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3fc186c-b909-4a28-a341-2226d91b0aa4
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Create and Modify an Adapter Group
One of the new features of Single Sign-On (SSO) is the ability to create and modify adapter groups. As the name implies, an adapter group is a collection of adapters. You can use adapter groups to organize security settings and other properties for your adapters.  
  
### To create and modify an adapter group  
  
1.  Create the adapter group by using a call to the ssops tool.  
  
     In the associated XML file, you must set the group flag as an adapter group.  
  
2.  Add one or more adapters to the adapter group by using `ISSOPSAdmin.AddAdapterToAdapterGroup`.  
  
     At this point, your adapter group is ready to work as intended. If necessary, you can view the full list of associated adapters by using `ISSOPSAdmin.GetAdaptersForAdapterGroup`.  
  
3.  You can modify the settings of your adapter group using `ISSOPSAdmin.SetAdapterProperties`.  
  
4.  When you are finished, you can remove the adapter from the adapter group using `ISSOPSAdmin.RemoveAdapterFromAdapterGroup`.  
  
5.  Finally, you can delete the adapter group by using `ISSOAdmin.DeleteApplication`.  
  
     You may choose instead to delete the adapter group by using the `-delete` command of the ssops tool.  
  
## See Also  
 [Synchronizing Passwords](../esso/synchronizing-passwords.md)