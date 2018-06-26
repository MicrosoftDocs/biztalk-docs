---
title: "Configure the SOAP action for the SAP system in BizTalk | Microsoft Docs"
description: Enter a SOAP action in Expression shape, or use the WCF-Custom or WCF-SAP adapter in the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76084bc5-7a10-4c4c-be22-bee83779a011
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the SOAP action for the SAP system
To perform any operation on the SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], adapter users must specify a SOAP action. The SOAP action communicates to the adapter what action should be performed. You can specify the SOAP action either at design time or at run time. However, if you specify the SOAP action both at design time and run time, the action you specified at design time will be overridden.  
  
 For more information about specifying SOAP action, see [Specifying SOAP Actions for WCF Send Adapters](../../core/specifying-soap-actions-for-wcf-send-adapters.md).
  
## Enter SOAP Action at Design Time  
 For design time, you must specify the SOAP action as part of orchestration by including an expression shape.  
  
 
1.  In the BizTalk orchestration, include an Expression shape by dragging it from the **BizTalk Orchestration** toolbox.  
  
2.  Double-click the **Expression** shape to open the BizTalk Expression Editor.  
  
3.  Specify the action in the BizTalk Expression Editor. For example:  
  
    ```  
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET"  
    ```  
  
     For more information about the **Expression** shape and the BizTalk Expression Editor, see [How to Create Expressions](../../core/how-to-create-expressions.md).
  
## Enter SOAP Action at Run Time  
 For run time, you can specify the SOAP action as part of the WCF-Custom or WCF-SAP port configuration.  
  
### Enter a SOAP action for the WCF-Custom port  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  
  
3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
4. In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.  
  
5. In the **Action** text box, specify the SOAP action for the operation. You can specify the action in the following ways:  
  
   -   **By using the single action format**. Use this format if the WCF-Custom port sends and receive messages for a single operation. For example:  
  
       ```  
       http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
       ```  
  
   -   **By using the action mapping format**. Use this format if a single WCF-Custom port sends and receives messages for more than one operation. For example, if a single WCF-Custom port sends and receives messages for Op1 (to invoke RFC_CUSTOMER_GET RFC) and Op2 (to invoke BAPI_SALESORDER_CREATEFROMDAT2 BAPI), the SOAP action can be specified in the following manner:  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
         <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
       </BtsActionMapping>  
       ```  
  
        This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.  
  
        The format for the SOAP action is different for each operation. For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).
  
### Enter a SOAP action for the WCF-SAP port  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then click **Send Ports**. In the right pane, you can choose to create a port or select an existing port.  
  
4. In the port properties dialog box, from the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.  
  
5. In the transport properties dialog box, click the **General** tab.  
  
6. In the **Action** text box, specify the SOAP action for the operation. You can specify the action in the following ways:  
  
   -   **By using the single action format**. Use this format if the WCF-Custom port sends and receive messages for a single operation. For example:  
  
       ```  
       http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
       ```  
  
   -   **By using the action mapping format**. Use this format if a single WCF-Custom port sends and receives messages for more than one operation. For example, if a single WCF-Custom port sends and receives messages for Op1 (to invoke RFC_CUSTOMER_GET RFC) and Op2 (to invoke BAPI_SALESORDER_CREATEFROMDAT2 BAPI), the SOAP action can be specified in the following manner:  
  
       ```  
       <BtsActionMapping>  
         <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
         <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
       </BtsActionMapping>  
       ```  
  
        This approach provides greater flexibility in terms of specifying a set of actions and hence enabling messages belonging to different action types to flow through the same port.  
  
        The format for the SOAP action is different for each operation. For more information about action format for each operation, see [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).
  
## See Also  
[Building blocks to create SAP applications](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)