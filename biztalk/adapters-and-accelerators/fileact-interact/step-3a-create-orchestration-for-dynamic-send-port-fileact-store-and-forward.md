---
description: "Learn more about: Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario"
title: "Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5675d476-ad36-4bbc-8e87-786edc9c805d
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario
Before you begin the steps in this section, you must complete the steps in the [Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md) section.  
  
### To Create an Orchestration  
  
1.  Create the Receive shape that subscribes to all of the messages of message type Sw-ExchangeSnFRequest.  
  
2.  Add an Expression shape to get all of the required values from the ExchangeRequestSnF message. Refer to the following Expression Shape sample:  
  
    ```  
    ExchangeSnFRequestDoc=ExchangeSnFRequest;  
    AcquireQueuePath="/Sw-ExchangeSnFRequest/Sw-SnFRequest/Sw-SnFOpRequest/Sw-AcquireSnFRequest/";  
  
    QueueNameNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath + "SwInt-Queue");  
    SessionModeNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-SessionMode");  
    ForceAcquireNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-ForceAcquire");  
    OrderByNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-OrderBy");  
    RecoveryModeNode=ExchangeSnFRequestDoc.SelectSingleNode(AcquireQueuePath+ "Sw-RecoveryMode");  
  
    QueueName=QueueNameNode.InnerText;  
    SessionMode=SessionModeNode.InnerText;  
    ForceAcquire=ForceAcquireNode.InnerText;  
    OrderBy=OrderByNode.InnerText;  
    RecoveryMode=RecoveryModeNode.InnerText;  
  
    MessageFormat="FileactMessage";  
    IsPull=true;  
  
    ```  
  
3.  Construct a message of type PullSnFRequest and the URL for Dynamic Send. Refer to the Assignment Shape of Construct Message sample:  
  
    ```  
    PullMessage = new System.Xml.XmlDocument();  
    PullMessage.LoadXml(@"<Sw-PullSnFRequest/>");  
    PullRequest = PullMessage;  
  
    DynamicPull(Microsoft.XLANGs.BaseTypes.Address) = "FILEACT://localhost/" + QueueName + "/" + SessionMode + "/" + ForceAcquire + "/" + OrderBy + "/" + RecoveryMode + "/" + MessageFormat;  
  
    ```  
  
4.  In this sample, PullMessage is a message of type Sw-PullSnFRequest.  
  
5.  Add a Send shape to send the PullMessage (pull request).  
  
6.  Add a request-response port for sending the pull message and for receiving the pull response with the dynamic binding.  
  
7.  Connect the Send shape with the port created in the previous step.  
  
8.  Add a Receive shape to receive the PullResponse (message of type PullSnFResponse) and then connect the Receive shape with the port previously created.  
  
9. Send the response to the respective folder using a Send shape.  
  
10. Add all of these activities (sending a pull request and receiving the response) in a loop if you want to pull all of the messages.  
  
11. Add an Expression shape CheckQueueEmpty to keep pulling until the time queue is empty. Refer the following Expression Shape sample:  
  
    ```  
    PullResponseDoc=PullResponse;  
    PullResponseNode=PullResponseDoc.SelectSingleNode("/Sw-PullSnFResponse/SwGbl-Status/SwGbl-StatusAttributes/SwGbl-Code");  
    if(PullResponseNode !=null && PullResponseNode.InnerText=="Sw.SnF.QueueEmpty")  
    {  
        IsPull=false;  
    }  
  
    ```  
  
12. This will set the IsPull = false, once the queue is empty.  
  
## See Also  
 [Step 3B: Bind the orchestration with dynamic send port for FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-bind-orchestration-with-dynamic-send-for-fileact-store-and-forward.md)
