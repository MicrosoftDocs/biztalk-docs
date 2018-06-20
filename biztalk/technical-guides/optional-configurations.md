---
title: "Optional Configurations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f4b0b51-2cad-4cb5-b6cd-4db92bd199fa
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optional Configurations
After you import the BizTalk Server Management Pack, the navigation pane of the Monitoring pane displays the object types that are discovered automatically. For a list of object types, see [Objects the Management Pack Discovers](../technical-guides/objects-the-management-pack-discovers.md) section. You can modify the default discovery configuration of objects discovered by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack. You use the overrides feature of Operations Manager 2007 R2/2012 to change configuration settings.  
  
 For an object type that is not automatically discovered, you can enable setting for automatic discovery in the **Authoring** pane in the Operations Console.  
  
#### To use an override to change the setting for automatic discovery  
  
1. In the Authoring pane, expand **Management Pack Objects**, and then click **Object Discoveries**.  
  
2. On the Operations Manager toolbar, click **Scope**, and filter the objects that appear in the details pane to include only BizTalk Server objects.  
  
3. In the details pane, click the object type you want to change the setting for.  
  
4. On the Operations Manager toolbar, click **Overrides**, click **Override the Object Discovery**, and then click either **For all objects of type:** \<*name of object type*\>, **For a group, For a specific object of type:** \<*name of object type*\>, or **For all objects of another type**.  
  
5. In the **Override Properties** dialog box, click the **Override** box for the **Enabled** parameter you want to change.  
  
6. Under **Management Pack**, click **New** to create an unsealed version of the Management Pack, and then click **OK**.  
  
   After you change the override setting, the object type will be automatically discovered and will appear in the Monitoring pane under [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
   For information about setting overrides, see [Overrides in Operations Manager 2007 R2/2012](http://go.microsoft.com/fwlink/?LinkId=86870) (http://go.microsoft.com/fwlink/?LinkId=86870).