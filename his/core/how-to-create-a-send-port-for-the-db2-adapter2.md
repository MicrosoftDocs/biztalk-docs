---
title: "How to Create a Send Port for the DB2 Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3cd360fc-2192-48ba-b965-bf5028bfa597
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Send Port for the DB2 Adapter
You create a send port for the BizTalk Adapter for DB2 by using the BizTalk Server Administration console. You must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, you must have appropriate permissions in the Single Sign-On (SSO) database.  
  
### To configure a send port  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft BizTalk Server 2013**, and then click **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Group**, expand **Applications**, and then select the application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
     The **Send Port Properties** dialog box appears.  
  
4.  In the **Transport Type** field, select **DB2**.  
  
5.  Click **Configure**.  
  
     The **DB2Transport Properties** dialog box appears.  
  
6.  Configure the following properties:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**BulkCopyBatchSize**|The **BulkCopyBatchSize** property instructs the Adapter the number of rows to process per batch transaction. This **optional** property accepts an **integer** value. The default value is **20**. A value of **0** instructs the Adapter to process all rows in a single batch.|  
    |**CommandTimeout**|The **CommandTimeout** property sets the wait time before the Adapter terminates an attempt to execute a command and then generate an error. This **optional** property accepts an **integer** value. The default value is **30** seconds. A value of 0 indicates no limit (an attempt to execute a command will wait indefinitely).|  
    |**Connection String**|The name of a connection string that is used to connect to the DB2 database.<br /><br /> To configure a new or existing Connection String, click the ellipsis (**…**). This starts the Data Source Wizard.<br /><br /> To access Help, click **Help** on the wizard pages, or open the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Help and look in [Data Source Wizard (DB2)](../core/data-source-wizard-db2-2.md).|  
    |**DB2 Set Registers**|The **DB2 Set Registers** property instructs the Adapter to execute one or more SQL SET statements. This optional property accepts a **string** value. The default value is an **empty string**, which denotes no statement. The supported syntax is a semi-colon delimited list of SET statement commands with a comma separate list of SET statement values “\<SET command 1> space \<SET value 1> semi-colon; \<SET command 2> space \<SET value a> comma \<SET value b> semi-colon”). For example, enter “SET CURRENT PATH 'DSN8910', 'HISDEMO'”.|  
    |**Document Target Namespace**|The target namespace that is used in the XML documents that are sent to DB2.|  
    |**Response Root Element Name**|The root element name that is used in the XML documents that are received from DB2. (This property may be empty for a one-way port.)|  
    |**URI**|Uniform resource identifier. A name to identify the send port location. Default is DB2://.|  
    |**UseBulkCopy**|The **UseBulkCopy** property instructs the Adapter to process send port INSERT commands in bulk copy mode to improve performance. This **optional** property accepts a **Boolean** value. The default value is **false**.|  
  
7.  Click **OK** to return to the **Send Port Properties** dialog box.  
  
8.  In the **Send Handler** field, select the host instance on which the send adapter is running.  
  
9. In the **Send Pipeline** field, select the pipeline that processes messages that are sent through this port. To configure a Send Pipeline, click “**...**”.  
  
     For more information, click **Help** on the property pages.  
  
10. You can configure additional properties by clicking the following tabs: **Transport Advanced Options**, **Backup Transport**, **Outbound Maps**, **Filters**, **Certificate**, and **Tracking**.  
  
     For more information click **Help** on these tabs.  
  
11. When you are finished with configuration, click **OK** to close the **Send Port Properties** dialog box and return to the BizTalk Server Administration console tree.  
  
12. In the **Send Ports** window, right-click the send port in the **Name** column and select **Enlist**.  
  
13. Right-click the send port in the **Name** column and select **Start**.  
  
## See Also  
 [Data Source Wizard (DB2)](../core/data-source-wizard-db2-2.md)