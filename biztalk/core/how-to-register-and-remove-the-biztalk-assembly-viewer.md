---
title: "How to Register and Remove the BizTalk Assembly Viewer | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f80b906-0a9e-4bcd-984d-db4550f2e51f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Register and Remove the BizTalk Assembly Viewer
The BizTalk Assembly Viewer is not registered automatically during BizTalk Server setup. To register or remove the BizTalk Assembly Viewer, follow these steps.  
  
### To add Assembly Viewer to the Windows registry  
  
1.  From the **Start** menu, click **Run**.  
  
2.  In the Run dialog box, type **cmd**.  
  
3.  From the command line, navigate to \<*BizTalk Server Installation Folder*\>\Developer Tools\ where BTSAsmExt.dll resides.  
  
4.  At the command line, type:  
  
     regsvr32 BTSAsmExt.dll  
  
5.  To begin using Assembly View, log off and then log back onto the computer.  
  
### To remove Assembly Viewer from the Windows registry  
  
1.  From the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**.  
  
3.  From the command line, navigate to \<*BizTalk Server Installation Folder*\>\Developer Tools\ where BTSAsmExt.dll resides.  
  
4.  At the command line, type:  
  
     regsvr32/u BTSAsmExt.dll  
  
5.  To complete the removal, log off and then log back onto the computer.  
  
## See Also  
 [Viewing Assemblies with the BizTalk Assembly Viewer](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)