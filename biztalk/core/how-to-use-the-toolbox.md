---
description: "Learn more about: How to Use the Toolbox"
title: "How to Use the Toolbox"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Use the Toolbox
You create a pipeline by dragging components (shapes) from the Toolbox to the design surface. Pipeline Designer helps you assemble valid pipelines by placing certain restrictions on the creation process. You can only select Toolbox components that apply to the pipeline type you are creating. For example, a receive pipeline will show decoders, disassemblers, and validators as valid Toolbox components, while encoders and assemblers will be disabled (dimmed).  
  
 In addition, stages can accept only valid components. For example, you cannot drag an encoder component to an Assemble stage. When you drag a component near a valid drop location, an arrow appears, indicating the point where the component can be inserted.  
  
 If you drag a valid component onto a stage that is collapsed, pause the mouse over the stage for a few seconds to expand it, and then drop the component into the stage.  
  
 Adding a custom component to the Toolbox in Pipeline Designer is similar to the standard Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] procedure.  
  
 **Start and End Shapes**  
  
 **Start** and **End** shapes appear as bullets on all pipelines. They are provided on the design surface for visual organization only. There is only one of each, and they can neither be added nor deleted. The **Start** and **End** shapes do not appear in the Toolbox.  
  
### To add a pipeline component to the Toolbox  
  
1.  On the **Tools** menu, click **Choose Toolbox Items**.  
  
     —Or—  
  
     Right-click the Toolbox and then click **Choose Items**.  
  
2.  In the **Customize Toolbox** dialog box, click the **BizTalk Pipeline Components** tab.  
  
     A dialog box displays the compatible pipeline components. You can navigate through the categories by clicking the tabs at the top of the dialog box.  
  
3.  Select the component you want to add to the Toolbox.  
  
4.  Click **OK**. The component will appear on the **BizTalk Pipeline Components** tab of the Toolbox.  
  
### To remove a pipeline component from the Toolbox  
  
-   Open the **Customize Toolbox** dialog box (as in the preceding procedure) and clear the component to be removed.  
  
     A component remains registered even after it has been removed from the Toolbox.  
  
## See Also  
 [How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md)   
 [How to Open a Pipeline](../core/how-to-open-a-pipeline.md)   
 [How to Navigate with the Keyboard](../core/how-to-navigate-with-the-keyboard.md)   
 [Creating Pipelines with Pipeline Designer](../core/creating-pipelines-with-pipeline-designer.md)
