---
title: "How to Configure the Transform Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [Orchestration Designer], Transform shape"
  - "Transform shape [Orchestration Designer]"
ms.assetid: ca81d153-77a6-4bcc-b14f-8f48469fffe0
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Transform Shape
![](../core/media/ebiz-orch-transform.gif "ebiz_orch_transform")  
Transform shape  
  
 Transforms are only used when you construct messages, so your **Transform** shape always appears inside a **Construct Message** shape. You can drop the **Construct Message** shape on the design surface and then drop the **Transform** shape inside it, or you can simply drop the **Transform** shape on the design surface, and Orchestration Designer will create the enclosing **Construct Message** shape for you.  
  
> [!NOTE]
>  Any source or destination message in a **Transform** must be based on a schema.  
  
## Procedure  
  
#### To configure a Transform shape  
  
1.  In the Properties Window, click the **Ellipsis** (**...**) button for the **Input Messages**, **Output Messages**, or **Map Name** property.  
  
2.  Use the **Transform Configuration** dialog box to configure the **Transform** shape.  
  
> [!NOTE]
>  A **Transform** shape can exist only within a **Construct Message** shape. If you drag a **Message Assignment** shape anywhere else on the design surface, a new **Construct Message** shape will be created.  
  
### Important Performance Considerations  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] optimizes the ability to perform transforms on large messages by streaming the document into memory while applying the transform as opposed to loading the entire document into memory at once. This optimization permits the mapping/transformation of much larger documents than was possible with earlier versions of BizTalk Server. A limitation of this optimization occurs when an orchestration accepts multiple inputs and/or outputs to transform shapes.  
  
 If an orchestration accepts multiple inputs and/or outputs to transform shapes then document streaming is not performed and memory use is increased considerably. One possible workaround to this issue would be to apply the transform or transforms in a receive pipeline so that the orchestration never accepts more than a single input or a single output to a transform shape.  
  
### New/Existing Map File?  
 In this section, you can click either the **New Map** or the **Existing Map** option button to select a map to assign to the **Transform** shape.  
  
 Use the **Name** field below the selected option button to specify a map. If you selected **New Map**, you can type a designation for the map you want to assign. When you use the **New Map** option, you must specify the fully qualified name of the map in the text box. The text box displays an example of such a name by default, because it is pre-populated with a unique identifier name based on the project namespace and **Transform** shape name: \<Project namespace\>.\<Transform shape name\>_Map (for example, MyProject.Transform3_Map).  
  
 If you selected **Existing Map**, click the Down arrow in the **Name** field to select which map file to use. This list box displays an alphabetically sorted list of all the existing maps available in the project. In this list, if you click the text \<Select from referenced assembly\>, the **Select Artifact Type** dialog box is displayed. For more information about the selections it makes available, see [How to Use the Select Artifact Type Dialog Box](../core/how-to-use-the-select-artifact-type-dialog-box.md).  
  
### Select Source and Destination Messages  
 Use this part of the **Transform Configuration** dialog box to configure the map you selected in the **New/Existing Map File?** section. If you selected **New Map** in that section, you create that map by configuring it in this section.  
  
 If you selected **Existing Map**, you can use this section to do one of two things:  
  
- Select an existing map to reuse as-is in the current transform.  
  
- Select an existing map in order to change (reconfigure) it, and then use it in its new configuration in the current transform.  
  
  Specify source and destination messages by using the **Source Messages** and **Destination Messages** grid controls. You can use these grid controls to change the map file in several ways. If you delete a message (a row in either grid control), add a message, or select a message of a different type, you alter the structure of the map. When you alter the structure of a map, all other transforms that use it must be changed to match the new structure of the map. Other changes, such as removing a message and inserting in its place a message of the same type, do not alter the structure of the map.  
  
  The **Source Messages** and **Destination Messages** grid controls are identical in appearance and behavior. Each grid control has two columns: Message and Type. You populate the grid controls by selecting messages in the Message column. (You add data only into the Message column, because the Type column is read-only.) The cells in the Message column have drop-down lists populated with message instances that are within scope for the current orchestration.  
  
  You can select a row in either grid control by clicking the *right arrow* (>) button at the left side of the grid control. After you have selected a row, you can delete it by pressing the DELETE key. Deleting a row (a message) alters the structure of the map file that contained it. You can modify only map files that are local to the project.  
  
### When I click OK, launch the BizTalk Mapper  
 Clicking **When I click OK, launch the BizTalk Mapper** opens BizTalk Mapper automatically when you click **OK** to close the **Transform Configuration** dialog box and save your changes. You cannot save changes, however, if required information is missing. In this case, finish filling out the fields in the dialog box and then click **OK**.  
  
## See Also  
 [About Maps](../core/about-maps.md)   
 [Constructing Messages](../core/constructing-messages.md)   
 [How to Use Expressions to Dynamic Transform Messages](../core/how-to-use-expressions-to-dynamic-transform-messages.md)