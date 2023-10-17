---
description: "Learn more about: Working in Orchestration Designer"
title: "Working in Orchestration Designer"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Working in Orchestration Designer
After you have started a BizTalk project, you can create new orchestrations and add existing orchestrations to the project. See the following procedures to create and save an orchestration, to add an existing orchestration to a project or remove one from it, to change the name of an orchestration, and to set orchestration properties.  
  
### To create an orchestration  
  
1.  In Solution Explorer, right-click the project name, select **Add**, and then click **New Item**.  
  
2.  In the **Add New Item** dialog box, in the **Categories** pane, click **BizTalk Project Items**, and then in the **Templates** pane, click **BizTalk Orchestration**.  
  
3.  In the **Name** box at the bottom of the dialog box, supply a name for the orchestration, and then click **Add**.  
  
     The new orchestration is created and displayed in Orchestration Designer, and a corresponding .odx file is created and displayed in Solution Explorer.  
  
### To add an existing orchestration to a project  
  
1.  In Solution Explorer, right-click the project name, click **Add**, and then click **Existing Item**.  
  
2.  In the **Add Existing Item** dialog box, navigate to the directory containing the orchestration, select the orchestration, and then click **Add**.  
  
     The orchestration is added to the project.  
  
    > [!NOTE]
    >  When you add an existing file, the file is copied to your project. (The file is not simply added by reference.) If you change the file in your project, the original file is left unchanged.  
  
### To change the name of an orchestration  
  
1.  In Solution Explorer, right-click the .odx file you want to change, and then click **Rename**.  
  
2.  Type the new file name you want, and then press ENTER.  
  
    > [!NOTE]
    >  When you change the name of an .odx file, you might also want to change the name of the orchestration type by clicking on the design surface to bring up the Properties window and changing the value of the **Typename** property of the orchestration.  
  
### To save an orchestration  
  
-   On the **File** menu, click **Save \<orchestration name\>**.  
  
    > [!NOTE]
    >  Orchestration files are saved as UTF-8.  Schemas, maps, and pipelines are saved as UTF-16.  
  
### To remove an orchestration from a project  
  
-   In Solution Explorer, right-click the file you want to remove, and then click **Exclude From Project**.  
  
    > [!NOTE]
    >  To remove the orchestration from a project and permanently delete the file, click **Delete** instead.  
  
### To include an excluded orchestration in a project  
  
-   In Solution Explorer, click the **Show All** toolbar button, right-click the .odx file you want, and select **Include in Project**.  
  
### To set orchestration properties  
  
1.  Open the orchestration by double-clicking on the .odx file in the project, or by selecting the tab containing the orchestration in the Process Area.  
  
2.  In the Orchestration View window, select **Orchestration Properties**.  
  
     —Or—  
  
     Click the **Process Area** background of the Orchestration Design Surface.  
  
3.  In the Properties window, specify the following properties. Note that some properties appear only under certain circumstances.  
  
    > [!NOTE]
    >  The names of orchestrations, port types and multi-part message types must be unique within the scope of a module.  
  
    |Property|Description|  
    |--------------|-----------------|  
    |Batch|Determines whether an orchestration that is an atomic transaction can be batched with other instances.|  
    |Compensation|Specifies what type of compensation to perform on the orchestration.|  
    |Isolation Level|For transactional orchestrations, determines the degree to which data is accessible among concurrent transactions.|  
    |Module Exportable|Determines whether or not the module can be exported to BPEL4WS.|  
    |Module XML Target Namespace|The XML target namespace used when exporting types to BPEL4WS.|  
    |Namespace|Determines the name of the containing module that includes the orchestration and the orchestration types.|  
    |Orchestration Exportable|Indicates whether this orchestration is intended to be exportable to BPEL4WS.|  
    |Orchestration XML Target Namespace|The XML target namespace used when exporting this orchestration to BPEL4WS.|  
    |Retry|Specify whether to retry a transactional orchestration if it fails.|  
    |Timeout|The time in seconds until a transactional orchestration fails due to inactivity.|  
    |Transaction Identifier|Unique identifier for a transactional orchestration.|  
    |Transaction Type|Determines whether the orchestration is an atomic transaction, a long-running transaction, or is not transacted.|  
    |Type Modifier|Determines the scope of orchestration-level variables:<br /><br /> Private—Access to this orchestration is limited to the containing module.<br /><br /> Public—Access to this orchestration is not limited.<br /><br /> Internal—Access to this orchestration is limited to modules within the same project.|  
    |Typename|Determines the name of this orchestration within the containing module. **Note:**  If you to use a Typename that is the same as a root-level namespace, you may receive an error from Orchestration Designer when you define messages and variables based on the Typename and attempt to perform assign operations on them. For example, if you specify a Typename of System, and then define messages and variables like System.String, you may receive an error.|  
  
## See Also  
 [Orchestration Shapes](../core/orchestration-shapes.md)   
 [How to Add Shapes to Orchestrations](../core/how-to-add-shapes-to-orchestrations.md)   
 [How to Add Parameters to Orchestrations](../core/how-to-add-parameters-to-orchestrations.md)   
 [How to Use the Select Artifact Type Dialog Box](../core/how-to-use-the-select-artifact-type-dialog-box.md)
