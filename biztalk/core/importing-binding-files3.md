---
title: "Import JD Edwards OneWorld binding files | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 955bb3e1-3dbc-43ce-9126-205d838ae662
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing Binding Files

## Overview
Before you use the BizTalk Server to import a binding file, verify the following:  
  
-   The CLASSPATH is pointing to a specific location for the JD Edwards-specific files. Verify that the location of these files is the same on the new computer, or edit the binding file.  
  
-   The folders for the responses exist and are identical on the new computer, or edit the binding file.  
  
-   JD Edwards system passwords, if present in the configuration, are saved as ***** in the binding file. For more information, see [Deployment Limitations](../core/deployment-limitations2.md).  
  
> [!NOTE]
>  Deployment overwrites Receive Location configuration. When deploying a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.  
  
## Import the Binding Files  
  
1.  On the **Start** menu, point to **Program Files**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration** to start the BizTalk Server Administration Console.  
  
2.  Expand BizTalk Server Administration, expand **BizTalk Group**, and then expand **Applications**.  
  
3.  Right-click the desired application, point to **Import**, and then click **Bindings**.  
  
4.  In the **Import Bindings** dialog box, browse and select the binding files, and then click **Open**.  
  
## Cleaning the Target Computer  
Remove the send ports and the receive locations that are bound to the orchestration.  
  
## See Also  
 [Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [Import the JD Edwards OneWorld app](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)