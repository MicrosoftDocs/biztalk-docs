---
description: "Learn more about: How to Create a New Gateway Node"
title: "How to Create a New Gateway Node"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Create a New Gateway Node
Follow these steps to create and configure a new Gateway node in PeopleSoft Enterprise.  
  
### To create and configure a new gateway node  
  
1. In PeopleSoft, on the left panel, click the **Node Definitions** link.  
  
2. Click the **Add a New Value** tab.  
  
3. In the **Node Name** field, enter `MSEXTERNAL`, and then click **Add**.  
  
4. Click the **Node** tab, and enter the following information:  
  
   1. **Description:** Enter a description for the node.  
  
   2. **Node Type:** Select **External**.  
  
   3. **Routing Type:** Select **Implicit**.  
  
      ![Image that shows the Node Info tab.](../core/media/psadapter-34-task-gatewaynodeconnector.gif "PSAdapter_34_Task_GatewayNodeConnector")  
  
5. Click the **Connectors** tab, and enter the following information:  
  
   1. **Gateway ID:** Enter `LOCAL`.  
  
   2. **Connector ID:** Enter `HTTPTARGET`.  
  
      ![Image that shows the Connectors tab.](../core/media/psadapter-35-task-gatewayhttptarget.gif "PSAdapter_35_Task_GatewayHTTPTarget")  
  
6. Click the **Lookup** icon.  
  
7. Under **Connector ID**, click the **HTTPTARGET** link.  
  
    ![Image that shows the HTTPTARGET link.](../core/media/psadapter-36-task-gatewayconnectorid.gif "PSAdapter_36_Task_GatewayConnectorID")  
  
8. On the **Properties** tab, enter the following information:  
  
   1.  **Header:** Enter `Y`.  
  
   2.  **HTTPPROPERTY:** Enter `POST`.  
  
   3.  **PrimaryURL:** Enter the IP address and port of the target computer (the development computer).  
  
   > [!NOTE]
   >  The **Receive Port** was previously set.  
  
    ![Image that shows where to enter the IP address and port.](../core/media/psadapter-37-task-gatewaynodereceiveport.gif "PSAdapter_37_Task_GatewayNodeReceivePort")  
  
## See Also  
 [Creating a PeopleSoft HTTP Host and Port](../core/creating-a-peoplesoft-http-host-and-port.md)
