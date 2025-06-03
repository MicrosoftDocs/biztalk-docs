---
description: "Learn more about: How to Test the HTTP Node"
title: "How to Test the HTTP Node"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Test the HTTP Node
Follow these steps to test the HTTP node.  
  
### To test the HTTP node  
  
1.  In PeopleSoft Enterprise, navigate to **PeopleTools**, **Integration Broker**, **Monitor**, **Monitor Message**.  
  
     ![Image that shows the Monitor Message screen.](../core/media/psadapter-40-task-gatewaytestnode.gif "PSAdapter_40_Task_GatewayTestNode")  
  
2.  Click the **Node Status** tab.  
  
3.  In the **Message Node Name** field, enter `MSEXTERNAL`, and then click the **Lookup** icon.  
  
4.  Under **Message Node Name**, select **MSEXTERNAL**.  
  
     A message appears and indicates that PeopleSoft is communicating through HTTP.  
  
     ![Image that shows where to select MSEXTERNAL.](../core/media/psadapter-41-task-gatewaytestsuccess.gif "PSAdapter_41_Task_GatewayTestSuccess")  
  
     If you do not receive the message, verify the following:  
  
    1.  The IP addresses and ports match between the receive port and the node.  
  
    2.  BizTalk Server is running.  
  
## See Also  
 [Creating a PeopleSoft HTTP Host and Port](../core/creating-a-peoplesoft-http-host-and-port.md)
