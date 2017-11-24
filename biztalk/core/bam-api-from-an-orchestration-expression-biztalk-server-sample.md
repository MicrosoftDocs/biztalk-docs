---
title: "BAM API from an Orchestration Expression (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, examples"
  - "examples, BAM"
  - "examples, orchestrations"
  - "BAM, examples"
ms.assetid: 341bc333-9bfc-484c-b431-9a71f9188792
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM API from an Orchestration Expression (BizTalk Server Sample)
This sample demonstrates how to:  
  
-   Use the BAM API from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration expression.  
  
-   Track repeating items inside a message as separate activity instances.  
  
-   Create a relationship between BAM data that is tracked by using a tracking profile, and BAM data tracked by using the BAM API.  
  
## Where to Find This Sample  
 You can find this sample at *\<Samples Path\>*\BAM\BamFromExpression.  
  
 The following table lists the files in this sample and describes their purpose.  
  
|File|Description|  
|----------|-----------------|  
|BamDefinition.xls|BAM definition stylesheet.|  
|BamDefinition.xml|BAM definition.|  
|BamFromExpression.btproj|[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] tracking file project.|  
|BamFromExpression.sln|[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution.|  
|Cleanup.bat|Batch file to undeploy the sample.|  
|InputMessage.xml|Input message.|  
|Orchestration1.odx|Orchestration.|  
|PoSchema.xsd|Purchase order schema.|  
|PropertySchema.xsd|Property schema.|  
|Setup.bat|Batch file to compile and deploy the sample.|  
|QueryBam.sql|SQL script.|  
  
## How to Use This Sample  
 Use the following procedures to create the tracking profile, run the sample, and view the results.  
  
#### To create the tracking profile  
  
1.  Open a command prompt and run *\<Samples Path\>*\BAM\BAMFromExpression\Setup.bat. If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], open the command prompt as administrator. Setup.bat initializes the BAM infrastructure for this sample, and deploys the BAM activity.  
  
2.  Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Tracking Profile Editor**. If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], right-click **Tracking Profile Editor** and then click **Run as administrator**.  
  
3.  In the left pane of the **Tracking Profile Editor** window, click **Click here to import a BAM Activity Definition**.  
  
4.  In the **BAM Activity Definition Name** section of the **Import BAM Activity Definition** dialog box, select **FromExpressionPo**, and then click **OK**.  
  
5.  In the right pane of the **Tracking Profile Editor** window, click **Click here to select an event source**.  
  
6.  In the **Assembly Name** section of the **Select Event Source Parent Assembly** dialog box, select **Microsoft.Samples.BizTalk.BamFromExpression**, and then click **Next**.  
  
7.  In the **Orchestration Name** section of the **Select Orchestration** dialog box, select **BamFromExpression.Orchestration1**, and then click **OK**.  
  
8.  Right-click the **Receive_1** shape, and then click **Message Payload Schema**.  
  
9. Expand **\<Schema\>**, expand **PurchaseOrder**, expand **From**, and then drag **PoID** in the right pane to **ActivityID** in the left pane.  
  
10. Drag the following elements from the right pane, and drop them onto the named nodes in the left pane:  
  
    |From|To|  
    |----------|--------|  
    |Name|From|  
    |State|State|  
    |City|City|  
    |Phone|Phone|  
    |Total|PoTotal|  
  
11. Click the folder icon with the arrow (![button with folder and up&#45;arrow](../core/media/abccd08b-2b01-49c6-80ed-a032bbbd10d4.gif "abccd08b-2b01-49c6-80ed-a032bbbd10d4")) to display the orchestration.  
  
12. Drag the **Receive_1** shape in the right pane to **Received** in the left pane.  
  
13. Drag the **Send_1** shape in the right pane to **Send** in the left pane.  
  
14. Save the tracking profile to *\<Samples Path\>*\BAM\BamFromExpression\ BamFromExpression.btt.  
  
15. On the **Tools** menu, click **Apply Tracking Profile**.  
  
#### To build and initialize this sample  
  
-   Deploy the BamFromExpression.btt tracking profile. For more information, see [How to Deploy Tracking Profiles with the Tracking Profiles Management Utility](../core/how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility.md).  
  
#### To run this sample  
  
-   Copy the file *\<Samples Path\>*\BamFromExpression\InputMessage.xml to *\<Samples Path\>*\BamFromExpression\Input.  
  
     In about 10 seconds the output message will appear in *\<Samples Path\>*\BamFromExpression\Output.  
  
#### To view the BAM data  
  
1.  Open SQL Server Management Studio.  
  
2.  In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.  
  
3.  Right-click **dbo.bam_FromExpressionPo_Completed**, and then click **Open Table**. If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.  
  
     The contents of the bam_FromExpressionPo_Completed table are displayed in the right pane. The one row, which has an activity ID of 123, represents the purchase order for $345 that was contained in the input message.  
  
4.  Right-click **dbo.bam_FromExpressionPoItem_Completed**, and then click **Open Table**. If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.  
  
     The contents of the bam_FromExpressionPoItem_Completed table are displayed in the right pane. The two rows, which have activity IDs 123_0 and 123_1, represent the items in the purchase order: Flash MC and Infrared Decoder.  
  
5.  Right-click **dbo.bam_FromExpressionPoItem_CompletedRelationships**, and then click **Open Table**. If you are using [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], click **Select top 1000 rows**.  
  
     The contents of the bam_FromExpressionPoItem_CompletedRelationships table are displayed in the right pane. Each row in the table represents a relationship between a FromExpressionPoItem activity and a FromExpressionPo activity. The value in the **ActivityID** column refers to the activity ID of the FromExpressionPoItem activity. The value in the **ReferenceData** column refers to the activity ID of the FromExpressionPo activity. In this case, the two records indicate that the Flash MC and Infrared Decoder items are associated with the purchase order for $345.  
  
#### To re-run the sample  
  
1.  Open a command prompt and run *\<Samples Path\>*\BAM\BamFromExpression\Cleanup.bat to remove the tracking profile and other BAM infrastructure. If you are using [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], open the command prompt as administrator.  
  
2.  Run *\<Samples Path\>*\BAM\BamFromExpression\Setup.bat to compile the sample and deploy it.  
  
## See Also  
 [Business Activity Monitoring (BizTalk Server Samples Folder)](../core/business-activity-monitoring-biztalk-server-samples-folder.md)   
 [Activity Relationships](../core/activity-relationships.md)