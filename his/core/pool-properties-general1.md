---
title: "Pool Properties: General1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_Pool_3270"
ms.assetid: a88c46b8-8a6f-432e-ad35-d2354f28958b
caps.latest.revision: 5
---
# Pool Properties: General
**Pool Name**  
 Enter a name for this pool.  
  
 **Comment**  
 Optionally, enter a comment of not more than 25 characters.  
  
 **Pool contains Display LUs with Associated Printers**  
 This option is intended for users whose host applications have a direct relationship between display LUs and printer LUs (that is, this applies to display-type pools only). With this option selected, all display LUs in the pool will be treated as though they have associated printer LUs. Also configure the display and printer LUs with the LU numbers that the host application is expecting.  
  
## Pool Properties: Display Model  
 **Display Model**  
 If you select **Display** for the LU Type, you can select a Display Model.  
  
 When an LU is assigned to a pool, the display model setting for the pool overwrites the setting of the LU, and the setting displayed in the **3270 LU Properties** dialog box is dimmed.  
  
 Some emulators can only emulate certain display models. For more information, see your emulator documentation. If there is a conflict between the Display Model setting for the pool and the Display Model setting for an LU in the pool, a message box appears. You can configure the individual LU setting to change or exclude the LU from the pool.  
  
 **Model can be overridden**  
 Select this check box to allow the user to override the display model type by using a 3270 terminal emulation program.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help2.md)