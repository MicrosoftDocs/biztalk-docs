---
title: "Considerations and Known Issues for TPE | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking Profile Editor, known issues"
  - "planning, Tracking Profile Editor"
  - "Tracking Profile Editor, planning"
ms.assetid: e96d85e0-e9ae-434a-b54e-5950f4a2b9c6
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations and Known Issues for TPE
You should consider the following issues when you work with tracking profiles and the TPE.  
  
## Naming Folders in the TPE  
 Note the following naming requirements when naming folders in Tracking Profile Editor:  
  
-   The length of the combination of folder name and data item instance values must not exceed 128 characters.  
  
-   For Continuation and ContinuationID folders, the naming of the folder is the key to correlating two orchestrations. For example, if Orchestration A is the parent of Orchestration B, Orchestration A contains a continuation folder whose name maps directly to the ContinuationID folder in Orchestration B.  
  
## Developing Orchestrations for the TPE  
 You cannot map an orchestration to a business activity if it starts or ends with an invalid shape. The Orchestration engine does not allow tracking for some shapes. They are:  
  
- Message Assignment  
  
- Transform  
  
- Group (Task)  
  
- Suspend  
  
- Loop (While)  
  
- Branch  
  
- Terminate  
  
- Throw  
  
- Catch  
  
- While shape  
  
  Use the following guidelines when mapping to business activities so that the Tracking Profile Editor and other BAM tools can use them:  
  
- For the Group shape, use a non-transactional Scope shape.  
  
- For the While shape, wrap it in a non-transactional Scope shape.  
  
- For the Terminate shapes, there is no workaround, because the end event of this shape never occurs in a normal scenario.  
  
- Do not start or end schedules with any of the shapes for which drag-and-drop operations are not permitted.  
  
## Applying Tracking Profiles that Monitor Running Processes  
 Updating a tracking profile can impact activity instances in progress if the activity includes a BAM continuation. Specifically, if the update to the tracking profile specifies a downstream interception of data for an activity item already recorded, it is possible that the original value will be overwritten. In essence, any single event stream will not be affected by the application of tracking profile updates because each stream object is tied to the specific version of the profile which was in place at the time the activity/stream started. However, because continuations are the means of correlating multiple event streams, streams not yet begun at the time of a profile update will pick up the changes in the update, thus introducing the possible data overwrite described. For more information about continuations, see [Activity Continuation](../core/activity-continuation.md) and [How to Create a Continuation](../core/how-to-create-a-continuation.md).  
  
## Tracking Profiles Without a Send or Receive Shape from Which to Draw Message Properties  
 Continuations track activities through context properties or payload data that are the same between activities. Properties such as Message ID, Service ID, and Instance ID change value between activities.  
  
 You can create tracking profiles to handle this scenario by using the following methods:  
  
-   If an orchestration sends a message through a dynamic binding to another orchestration, then a globally unique payload data value can be used for the continuation.  
  
-   If there is no unique payload data in the message, then the interchange ID of the message can be used. To use the interchange ID, you must track it on the same Receive shape. You cannot use the interchange ID if you create a new message, as the interchange ID changes when the new message is created. Tracking the interchange ID from any shape other than a Receive or Send shape is not reliable.  
  
-   You can also use message ID as long as the exact same message that is received from the pipeline is used in the orchestration, that is, the orchestration port is bound to a pipeline and a Receive shape and the message ID are tracked from that location. If you track the message ID from a different shape, then the message ID will be invalid for use in continuations.  
  
-   If an orchestration calls another orchestration and no message is passed, or an orchestration calls another orchestration but the callee does not have any Construct, Receive, or Send shape where payload data values can be retrieved, the user can use the instance ID. The instance ID for the called orchestrations does not change.  
  
-   If the orchestration loads another orchestration through an execution call rather than calling it directly, then there is no way to use any static message properties to track the activity. The user cannot enable a continuation. The only way to perform tracking in this instance is if a message is passed through the pipeline that contains unique payload data on which to perform the tracking.  
  
## You Cannot Use a Session ID as a Continuation Token for Pass-Through Pipelines  
 In a tracking profile, when you select items from a message payload, the tracking profile is bound to the schema of that message. In a pass-through pipeline, the schema name value is a null value. When BAM attempts to load the configuration by port name and schema name it cannot make the match to the session ID schema and no data is tracked by the engine.  
  
 For pass-through pipelines, you can either remove all payload tracking from the tracking profile or use XML pipelines if you do need to track the payload data.  
  
## Using Unique Port Names  
 When enumerating two-way ports, the TPE displays them as two logical ports, a send and a receive port. Each of these logical ports is displayed with the same name. BizTalk Server allows you to create one-way and two-way ports with the same name. For example, you can create a two-way port named "Port1" and then create a receive port with the same name. In these cases the TPE displays the receive port once and the two-way port twice, once as a receive port and once as a send port.  
  
 TPE will apply tracking profiles to both receive ports in this case. We recommend that ports be given unique names to help identify them properly.  
  
## Using TPE Orchestrations with a Parallel Shape as the First Shape  
 If you begin an orchestration with a Fork, Parallel, or Listen shape, you cannot map an activity ID on one of the branches. In cases of parallel processing you can map the ActivityID above the Fork shape. You can also let BAM generate the activity ID to avoid the issue of a parallel shape at the top of the orchestration.  
  
> [!IMPORTANT]
>  Mapping an activity to more than one path and also mapping the ActivityID to one path of the Fork shape causes an error when processing follows the path on which the ActivityID is not mapped.  
  
## Availability of Message Properties at Design Time  
 When creating tracking profiles, not all message properties are available. This is most likely to be encountered when the shape where the message properties are mapped from is at the top of an orchestration. In these instances, the value of the message properties is null.  
  
 An example of this is where the Listen shape is the first shape in an orchestration. When message properties are mapped from this shape, only the following properties have values: InstanceID, ServiceID and ServiceClassID. (MessageID is not in scope at this point and has a null value.)  
  
## You Cannot Map Shapes Inside a Loop Shape to Report a Milestone  
 The TPE blocks mapping sources contained from within a Loop shape to activities that are mapped to items that are outside of the loop.  
  
 Looping activities refers to actions that loop, or repeat, within an orchestration. It is possible to capture the events from actions that loop within an orchestration. To do this, you create another activity and map all of the new activity milestones and data inside the loop. This is necessary because the data processing in the loop will occur more than once per scheduled execution.  
  
 For example, if you have a purchase order with multiple line items that process in a loop, questions like “Which purchase orders have item prices of $100?" are ambiguous. Unambiguous questions are:  
  
 Which purchase orders have line items with a price of $100?  
  
 Which purchase orders have Total/Min/Max item prices of $100?  
  
 Creating unambiguous questions requires thinking of the line items as something separate from the purchase order. In the Tracking Profile Editor, the root activity (for example, a purchase order) maps to all actions outside the loop. The child activity (for example, a line item) maps to the actions inside the loop.  
  
 The typical approach to working with these types of constructs is to decompose the repeating loop and to have a related activity based on the inner activity that is related to the outer activity.  
  
 You need to use a payload item as the ActivityID for the root activity and have this payload item available in some of the messages inside the loop. Map the activity to the relationship node that displays under the child activity and name it as the root activity.  
  
## Tracking Profiles Spanning Multiple Applications  
 If a tracking profile spans multiple applications, the tracking profile must be deployed after all applications in the solution are deployed. If the tracking profile is not the last item deployed, you will receive the following message, "**Mapping source not found.**", when the deployment wizard calls BTTDeploy.exe.  
  
## Mapping Multiple BizTalk Server Artifacts to a Document Reference URL or MessageID Nodes  
 The TPE allows you to drag and drop from multiple BizTalk Server artifacts onto the same document reference URL or MessageID node.  
  
 In cases where multiple sources are mapped to the same item in a BAM activity, the last artifact that was encountered during BAM processing is the one that persists in the tracking data and can be viewed in the BAM portal.  
  
## Updating BTT Versions to Match BizTalk Solution Versions  
 BAM developers and administrators can maintain version synchronization between tracking profiles and BizTalk solutions by automating the update to the BTT file. To do this, modify the **Version** attribute in the **DataLevel** element of the BTT file. In the following sample element, you would modify the version information in the TargetAssemblyName and SchemaName attributes.  
  
```  
<DataLevel Name="City" SourceTypeSelected="Messaging Payload" TargetAssemblyName="TheImplementationOfOrderMgmt, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c5b33e44ffa4658b" SchemaName="TheImplementationOfOrderMgmt.PurchaseOrder,TheImplementationOfOrderMgmt, Version=1.0.0.0, Culture=neutral, PublicKeyToken=c5b33e44ffa4658b" SomXPath="/*[local-name()='<Schema>' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='PurchaseOrder' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='Header' and namespace-uri()='']/*[local-name()='ShipTo' and namespace-uri()='']/@*[local-name()='City' and namespace-uri()='']" XPath="/*[local-name()='PurchaseOrder' and namespace-uri()='http://TheImplementationOfOrderMgmt.PurchaseOrder']/*[local-name()='Header' and namespace-uri()='']/*[local-name()='ShipTo' and namespace-uri()='']/@*[local-name()='City' and namespace-uri()='']" IsBeginActivity="true" IsEndActivity="false">  
```  
  
## Some Orchestration Shapes Cannot be Tracked in the TPE  
 The orchestration ongine does not generate events for the following shapes and thus these shapes cannot be tracked or mapped in the TPE:  
  
-   Task  
  
-   All Branches  
  
-   Suspend  
  
-   Terminate  
  
-   Throw  
  
-   Catch  
  
-   MessageAssignment (because it is part of the Construct shape)  
  
-   Transform (because it is part of the Construct shape)  
  
-   Loop  
  
## TPE Not Retrieving Deployed Tracking Profiles  
 After an upgrade or redeployment you may experience difficulties in retrieving deployed tracking profiles. This can be caused by a mismatch in the manner in which the server name on which BizTalkMgmtDb database is stored in the registry.  
  
 The BizTalkMgmtDb is written to the registry during Group configuration. The TPE uses the entry to find the Primary Import database and to filter the tracking profiles.  
  
 During configuration it is possible to enter the server name in several formats. For example:  
  
- mgmtsvr1316267,15001\inst  
  
- MGMTSVR1316267\inst,15001  
  
  The TPE performs a basic string comparison when using the registry entry. To retrieve the deployed tracking profiles it is necessary to inspect the stored server and database names and enter them in the TPE **Set Management Database** dialog box.  
  
#### To determine the syntax for server and database names and enter it in the BizTalk Management database.  
  
1. Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**Custom Configuration Manager**. For information about using the **Custom Configuration Manager**, see [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).  
  
2. In the navigation pane, select **Group** to open the group configuration page.  
  
3. In the **Data Stores** grid, observe the formats of the **Server Name** and the **Database Name**.  
  
4. Open the TPE and select the **Tools** menu item.  
  
5. Select the **Set Management Database** menu item to open the **Set Management Database** dialog box.  
  
6. In the **SQL Server** text box, enter the server name that was used in the **Server Name** field of the **Data Stores** gridon the **Custom Configuration Manager** group page.  
  
7. In the **Database name** text box, enter the database name that was used in the **Database Name** field of the **Data Stores** gridon the **Custom Configuration Manager** group page.  
  
8. Click the **OK** button to save the entries.  
  
## See Also  
 [Using the TPE](../core/using-the-tpe.md)   
 [Tracking Profile Editor](../core/tracking-profile-editor.md)