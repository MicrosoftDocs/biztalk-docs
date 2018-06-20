---
title: "Configure the SOAP action for Oracle Database in BizTalk | Microsoft Docs"
description: Enter a SOAP action in Visual Studio, or use the WCF-Custom or WCF-OracleDB adapter in the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0d21cca-3907-4f99-af76-c1e7286e1bcf
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the SOAP action for Oracle Database
To complete any operation on the Oracle database using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], adapter users must enter a SOAP action. The SOAP action communicates to the adapter what action should be completed. You can enter the SOAP action either at design time or at run time. However, if you enter the SOAP action both at design time and run time, the action you enter at design time is overridden.  
  
 For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).  
  
## Enter SOAP Action from Visual Studio  
 From Visual Studio, you must specify the SOAP action as part of the orchestration by using an **Expression** shape.  
  
1.  In the BizTalk orchestration, include an **Expression** shape by dragging it from the **BizTalk Orchestration** toolbox.  
  
2.  Double-click the **Expression** shape to open the BizTalk Expression Editor.  
  
3.  Specify the action in the BizTalk Expression Editor. For example:  
  
    ```
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"  
    ```  
  
     For more information about **Expression** shape and the BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).  
  
## Enter SOAP Action from BizTalk Server Administration  
 From the BizTalk Server Administration console, you must specify the SOAP action as part of the WCF-Custom or WCF-OracleDB port configuration. 

#### Enter a SOAP action for the WCF-Custom port  
 
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, then expand **Applications**, then expand the application under which you want to create a port, and then click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  
  
3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
4. In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.  
  
5. In the **Action** text box, specify the SOAP action for the operation. You can specify the action in the following ways:  
  
   -   **By using the single action format**. Use this format if the WCF-Custom port sends and receive messages for a single operation. For example:  
  
       ```  
       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
       ```  
  
   -   **By using the action mapping format**. Use this format if a single WCF-Custom port sends and receives messages for more than one operation. For example, if a single WCF-Custom port sends and receives messages for Op1 (to insert records in the EMP table) and Op2 (to update records in the EMP table), the SOAP action can be specified in the following manner:  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
         <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
       </BtsActionMapping>  
       ```  
  
        This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.  
  
        The format for the SOAP action is different for each operation. For more information about action format for each operation, see [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).  
  
#### Enter a SOAP action for the WCF-OracleDB port  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-OracleDB adapter to the BizTalk Server Administration console. For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, then expand **Applications**, then expand the application under which you want to create a port, and then click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  
  
4. In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleDB port you added earlier, and then click **Configure**.  
  
5. In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.  
  
6. In the **Action** text box, specify the SOAP action for the operation. You can specify the action in the following ways:  
  
   -   **By using the single action format**. Use this format if the WCF-OracleDB port sends and receive messages for a single operation. For example:  
  
       ```  
       http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
       ```  
  
   -   **By using the action mapping format**. Use this format if a single WCF-OracleDB port sends and receives messages for more than one operation. For example, if a single WCF-OracleDB port sends and receives messages for Op1 (to insert records in the EMP table) and Op2 (to update records in the EMP table), the SOAP action can be specified in the following manner:  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
         <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
       </BtsActionMapping>  
       ```  
  
        This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.  
  
        The format for the SOAP action is different for each operation. For more information about action format for each operation, see [Messages and Message Schemas](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).
  
## See Also  
[Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)