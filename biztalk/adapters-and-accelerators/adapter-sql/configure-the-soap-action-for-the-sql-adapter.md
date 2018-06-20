---
title: "Configure the SOAP action for the SQL adapter in BizTalk | Microsoft Docs"
description: Enter a SOAP action in Visual Studio, or use the WCF-Custom or WCF-SQL adapter in the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: acd7f60b-c27f-4988-a67c-e56ef8d38f66
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the SOAP action for the SQL adapter
To perform any operation on SQL Server using the WCF-based [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must specify a SOAP action. The SOAP action communicates to the adapter what action should be performed. You can specify the SOAP action either from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. However, if you specify the SOAP action from both locations, the action you specified from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] will be overridden.  
  
 For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).
  
## Enter the SOAP action in Visual Studio  
 From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the SOAP action as part of the orchestration by using an **Expression** shape.  
  
1.  In the BizTalk orchestration, include an **Expression** shape by dragging it from the **BizTalk Orchestration** toolbox.  
  
2.  Double-click the **Expression** shape to open BizTalk Expression Editor.  
  
3.  Specify the action in BizTalk Expression Editor. For example:  
  
    ```  
    OutboundMessage(WCF.Action)="TableOp/Insert/dbo/Employee"  
    ```  
  
     For more information about the **Expression** shape and BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).
  
## Enter the SOAP action from the BizTalk Server Administration console  
 From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you can specify the SOAP action as part of the WCF-Custom or WCF-SQL port configuration.  
  
### Enter a SOAP action for the WCF-Custom port  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  
  
3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
4. In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.  
  
5. In the **Action** text box, specify the SOAP action for the operation. You can specify the action in the following ways:  
  
   -   **By using the single action format**. Use this format if the WCF-Custom port sends and receive messages for a single operation. For example:  
  
       ```  
       TableOp/Insert/dbo/Employee  
       ```  
  
   -   **By using the action mapping format**. Use this format if a single WCF-Custom port sends and receives messages for more than one operation. For example, if a single WCF-Custom port sends and receives messages for Op1 (to insert records in the Employee table) and Op2 (to update records in the Employee table), the SOAP action can be specified in the following manner:  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
         <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
       </BtsActionMapping>  
       ```  
  
        The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.  
  
        The format for the SOAP action is different for each operation. For more information about the action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).
  
### Enter a SOAP action for the WCF-SQL port  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Adding the SQL Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  
  
4. In the port properties dialog box, from the **Type** drop-down list, select the WCF-SQL adapter you added earlier, and then click **Configure**.  
  
5. In the transport properties dialog box, click the **General** tab.  
  
6. In the **Action** text box, specify the SOAP action for the operation. You can specify the action in the following ways:  
  
   -   **By using the single action format**. Use this format if the WCF-SQL port sends and receive messages for a single operation. For example:  
  
       ```  
       TableOp/Insert/dbo/Employee  
       ```  
  
   -   **By using the action mapping format**. Use this format if a single WCF-SQL port sends and receives messages for more than one operation. For example, if a single WCF-SQL port sends and receives messages for Op1 (to insert records in the Employee table) and Op2 (to update records in the Employee table), the SOAP action can be specified in the following manner:  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
         <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
       </BtsActionMapping>  
       ```  
  
        The action mapping approach provides greater flexibility in terms of specifying a set of actions, and hence enabling messages that belong to different action types to flow through the same port.  
  
        The format for the SOAP action is different for each operation. For more information about the action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).
  
## See Also  
[Building blocks to develop BizTalk applications with the SQL adapter](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)