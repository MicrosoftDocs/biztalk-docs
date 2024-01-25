---
description: "Learn more about: How to Use the Select Artifact Type Dialog Box"
title: "How to Use the Select Artifact Type Dialog Box"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Use the Select Artifact Type Dialog Box
An *item* is used to configure elements of an orchestration in Orchestration Designer. Examples of items are schemas, maps, pipelines, port types, and multi-part message types. When you develop an orchestration and its constituent parts such as port shapes, transform shapes, and messages, you may need to refer to items that do not reside in the current orchestration, but are in the current project or another project that has been compiled into a BizTalk Server assembly. You use the **Select Artifact Type** dialog box to locate and then specify items when configuring an element within an orchestration.  
  
 The **Select Artifact Type** dialog box is available from many locations in Orchestration Designer. You can select \<Select from referenced assembly\> in a drop-down list that displays configuration options; clicking this text opens the **Select Artifact Type** dialog box.  
  
 Before you can select an item, you must first select the element you want to configure.  
  
 You can use the **Select Artifact Type** dialog box for the following specific purposes:  
  
|Action|Purpose|  
|------------|-------------|  
|Select a pipeline|Select a pipeline for the pipeline property when configuring a port for direct (early) binding.|  
|Select a map|Select a map to use with a **Transform** shape.|  
|Select a schema|Select schemas in the project when creating multi-part message types.|  
|Select a port type|Refer to existing port types when creating a port.|  
|Select a multi-part message type|Refer to existing multipart types when creating messages.|  
|Select a .NET type|Refer to existing .NET types when creating variables or messages.|  
  
 **Reference pane**  
  
 The reference pane of the **Select Artifact Type** dialog box displays references in the current project and in other available assemblies. To select a reference in this pane, click it. To expand a container in this pane (such as the **Assemblies** container), click the plus sign (+) beside it.  
  
 **Item pane**  
  
 The item pane of the **Select Artifact Type** dialog box displays the items contained in the reference currently selected in the reference pane. The item pane has two columns, **Item** and **Qualified Name**, which display information about the items in the current reference.  
  
### To use the Select Artifact Type dialog box  
  
1.  Expand the **References** node in the left pane. The pane displays available projects and assemblies.  
  
2.  Expand the **Assemblies** node. One or more assemblies are listed, such as SYSTEM.DLL and MICROSOFT.BIZTALK.PIPELINES.DLL.  
  
3.  Click an assembly. If the assembly contains items, they are displayed in the right pane. The qualified name of an item is displayed in the right column of the right pane.  
  
    > [!NOTE]
    >  If the current project contains items, you can click it to view its items and select one.  
  
4.  To select an item in the right pane, click it and then click **OK** to exit the **Select Artifact Type** dialog box. This assigns that item as the type for the selected element. To close the **Select Artifact Type** dialog box without selecting and assigning an item, click **Cancel**.  
  
## See Also  
 [Orchestration Shapes](../core/orchestration-shapes.md)   
 [How to Add Shapes to Orchestrations](../core/how-to-add-shapes-to-orchestrations.md)   
 [How to Add Parameters to Orchestrations](../core/how-to-add-parameters-to-orchestrations.md)
