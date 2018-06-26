---
title: "How to Create a New Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, pipelines"
  - "pipelines, warnings"
  - "Pipeline Designer, warnings"
  - "pipelines, creating"
ms.assetid: bd95325e-1a72-4705-80f6-37ac092d11a3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a New Pipeline
You can add a pipeline template to your project to create a new pipeline.  
  
> [!WARNING]
>  You should not add a project that contains an implementation of a custom pipeline component to a solution that contains a project that uses that pipleine component. If you do, the next time you rebuild the solution you will get an error saying the output dll is being used by another process.  
  
### To create a new pipeline  
  
1. In Solution Explorer, select the project in which you want to create the pipeline.  
  
2. On the **Project** menu, click **Add New Item**.  
  
3. In the **Add New Item** dialog box, select a **Receive Pipeline** or **Send Pipeline** template by clicking it once.  
  
   > [!NOTE]
   >  If you double-click the template, the pipeline will automatically be created with the default name that appears in the **Name** field.  
  
4. In the **Name** field, type a name for the pipeline.  
  
5. Click **Open**.  
  
    The new pipeline appears in Solution Explorer. The design surface displays pipeline stages and a default set of components.  
  
   For information about adding pipeline components to the pipeline, see [How to Add a Component to a Pipeline](../core/how-to-add-a-component-to-a-pipeline.md).  
  
## See Also  
 [How to Open a Pipeline](../core/how-to-open-a-pipeline.md)   
 [How to Save a Pipeline](../core/how-to-save-a-pipeline.md)   
 [How to Use the Toolbox](../core/how-to-use-the-toolbox.md)   
 [How to Navigate with the Keyboard](../core/how-to-navigate-with-the-keyboard.md)   
 [Creating Pipelines with Pipeline Designer](../core/creating-pipelines-with-pipeline-designer.md)