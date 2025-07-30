---
description: "Learn more about: How to Configure the Integration Gateway and HTTP Output Connector"
title: "How to Configure the Integration Gateway and HTTP Output Connector"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
ms.custom:
  - sfi-image-nochange
---
# How to Configure the Integration Gateway and HTTP Output Connector
Follow these steps to configure the Integration Gateway and HTTP Output Connector.  
  
### To create and configure a new gateway node  
  
1.  In a Web browser, open the PeopleSoft application.  
  
2.  Locate **PeopleTools**, select **Integration Broker**, and then select **Gateways**.  
  
3.  In the **Search By** field, type `LOCAL`, and then click **Search**.  
  
     ![Image that shows where to type LOCAL in the Search By field.](../core/media/psadapter-31-task-gatewaysearch.gif "PSAdapter_31_Task_GatewaySearch")  
  
4.  Enter `machine-name/PSIGW/PeopleSoftListeningConnector` into the **Gateway URL** entry.  
  
     ![Image that shows where to find the Gateway URL field.](../core/media/psadapter-32-task-gatewayurl.gif "PSAdapter_32_Task_GatewayURL")  
  
5.  Click **Refresh**, and then click **Save**.  
  
6.  Click the **Properties** link for **HTTPTARGET** to view the properties/value combination for that ID.  
  
     You can set the URL here, or at the Node Definition. For this discussion, set the URL at the Node level.  
  
     ![Image that shows where to view the properties/value combination](../core/media/psadapter-33-task-gatewaynodelevel.gif "PSAdapter_33_Task_GatewayNodeLevel")  
  
## See Also  
 [Creating a PeopleSoft HTTP Host and Port](../core/creating-a-peoplesoft-http-host-and-port.md)
