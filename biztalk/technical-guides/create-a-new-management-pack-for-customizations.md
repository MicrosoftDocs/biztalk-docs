---
title: "Create a New Management Pack for Customizations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ce1ffa0-57c7-41ce-b459-48c36522889e
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create a New Management Pack for Customizations
Most vendor management packs are sealed so that you cannot change any of the original settings in the management pack file. However, you can create customizations, such as overrides or new monitoring objects, and save them to a different management pack. By default, Operations Manager 2007 R2/2012 saves all customizations to the Default Management Pack. As a best practice, you should instead create a separate management pack for each sealed management pack that you want to customize.  
  
 Creating a new management pack for storing overrides has the following advantages:  
  
- It simplifies the process of exporting customizations that were created in your test and pre-production environments to your production environment. For example, instead of exporting the Default Management Pack that contains customizations from multiple management packs, you can export just the management pack that contains customizations of a single management pack.  
  
- You can delete the original management pack without first having to delete the Default Management Pack. A management pack that contains customizations depends on the original management pack. This dependency requires you to delete the management pack with customizations before you can delete the original management pack. If all of your customizations are saved to the Default Management Pack, you must delete the Default Management Pack before you can delete an original management pack.  
  
- It is easier to track and update customizations to individual management packs.  
  
  For more information about sealed and unsealed management packs, see [Management Pack Formats](http://go.microsoft.com/fwlink/?LinkID=198193) (http://go.microsoft.com/fwlink/?LinkId=198193). For more information about management pack customizations, see [Customizing Management Packs](http://go.microsoft.com/fwlink/?LinkID=198194) (http://go.microsoft.com/fwlink/?LinkID=198194).