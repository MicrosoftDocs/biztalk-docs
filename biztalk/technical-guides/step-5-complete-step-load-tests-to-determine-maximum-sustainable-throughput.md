---
title: "Step 5: Perform Step Load Pattern Tests to Determine Maximum Sustainable Throughput | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8056ced6-1f04-4be2-878a-48a427a93dad
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Perform Step Load Pattern Tests to Determine Maximum Sustainable Throughput
The simplest method for determining the Maximum Sustainable Throughput (MST) of a BizTalk Server solution with Visual Studio load testing is to perform a step load pattern and compare the total Documents received per second to the total Document processed per second. As long as the average total documents processed per second is greater than or equal to the average total documents received per second for the duration of the test, then the load is considered sustainable. If the average total documents received per second is greater than the average total documents processed per second for the duration of the test, then the load is not considered sustainable, and this will be evidenced by a corresponding growth in the value of the BizTalk:Message Box:General Counters\Spool Size counter. Over time, when a BizTalk Server application receives more documents than it can process, the unprocessed documents will accumulate in the MessageBox database, which will eventually induce a throttling condition and significantly degrade the performance of the BizTalk Server application.  
  
## Configure the Load Test with a Step Load Pattern Appropriate for your Application  
 Follow the steps in the topic [Step 3: Create a Load Test to Perform Multiple Unit Tests Simultaneously](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md) to create a load test that uses a step load pattern. Factors that impact the ability of the BizTalk Server Application to process documents in a timely fashion include:  
  
- **Number of BizTalk Server computers in your group** - Additional BizTalk Servers provide additional processing ability.  
  
- **Size of the messages being processed** - Larger messages require additional processing resources.  
  
- **Amount of document mapping performed** -Mapping requires additional processing resources.  
  
- **Receive or send pipelines required by the application**. - Complex pipelines require additional processing resources.  
  
- **Adapters and/or Accelerators used by the BizTalk Server application** – Some adapters and/or accelerators require more processing resources than others.  
  
- **Amount of Message tracking required** – Message tracking is resource intensive.  
  
- **Number of and complexity of Orchestrations running in the BizTalk Server Application** – Orchestrations can be very resource intensive.  
  
  When configuring the Step Load Pattern Test, modify the values specified for **Start user count** and **Maximum user count** to ensure that the number of messages specified for Start user count can be easily handled by the BizTalk Server application over time and likewise, the number of messages specified for Maximum user count is more than the BizTalk Server application can handle over time. See [Add a Load Test and Configure the Load Test Scenario, Counter Sets, and Run Settings](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_StepLoadTest) for information about editing the load pattern settings for the load test.  
  
## Ensure that the Correct Test Settings are Used for the Step Pattern Load Test  
 Configure the Load Test to use the **Test Settings** that you created in [Add A Test Settings File to the Solution to Run Tests and Collect Data Remotely](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_TestSettings).  
  
## Configure the Load Test with the Appropriate Performance Counters and run the Step Pattern Load Test  
 Follow the steps in [Add a Custom Counter Set to Measure BizTalk Server Key Performance Indicators (KPI)](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_BTSCounters) to add the necessary BizTalk Server performance counters which can be used to measure the performance of the BizTalk Server Application and determine at what point the BizTalk Server Application is no longer able to maintain the message load created by the Load Test Agents. This will be evidenced by the accrual of a backlog of messages in the Spool table as seen by an increased value for the BizTalk:Message Box:General Counters\Spool Size counter. If the value for this counter begins to increase significantly then you have likely exceeded the MST of your BizTalk Server Application. Once you have determined the number of messages at which the BizTalk Server Application is no longer able to process as many messages as it is receiving, make a note of the Documents received/Sec when this occurs. It is important to make a note of this value because the topic [Step 6: Perform Constant Load Pattern Tests to Verify Maximum Sustainable Throughput](../technical-guides/step-6-complete-load-pattern-tests-to-verify-maximum-sustainable-throughput.md) will describe how to run a constant pattern load test with a “Constant User Count” value that is somewhat smaller than the maximum sustainable Documents received/Sec value. This is done to verify that the BizTalk Server Application is capable of processing this number of messages over time. To view values for counter sets, first start the load test by right-clicking the test name (e.g. BTS_Messaging_Step) and then click the **Run Test** menu option. After Performance counters are initialized and the load test begins, Visual Studio will automatically switch focus to the Graphs window which allows you to display from 1 to 4 graphs simultaneously. If you are primarily interested in only viewing key performance indicators, as defined in [Add a Custom Counter Set to Measure BizTalk Server Key Performance Indicators (KPI)](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_BTSCounters), click the **Panels** dropdown list from the Load test menu and select the option for **One Panel**. Then click the drop-down list at the top of the chart and select **Key Indicators** to display values for the key Performance indicators in real time.  
  
> [!NOTE]  
>  Because certain default counter values will be displayed in the **Key Indicators** graph and because you will probably want to display counter values that you added to your custom counter set, you may want to start by manually deleting each of the counters displayed in the **Key Indicators** graph and then manually add counters from your custom counter set(s). For example, at the least, you would want to add at least the counters in the table below to your graph to determine how well the BizTalk Server environment is handling the load, and where any bottlenecks may be occurring:  
  
|Counter Category|Counter|Instance|Computer|  
|----------------------|-------------|--------------|--------------|  
|BizTalk:Message Box:General Counters|Spool Size|*BizTalk Server Message Box database*:*SQL Server Instance that houses the BizTalk Server Message Box database*|Any BizTalk Server in the group with the BizTalk Server Administration Console installed.|  
|BizTalk:Messaging|Documents received/Sec|RxHost (or name of the receive host)|*BizTalk Server Computer#1 in the BizTalk Server Group*|  
|BizTalk:Messaging|Documents received/Sec|RxHost (or name of the receive host)|*BizTalk Server Computer#2 in the BizTalk Server Group*|  
|BizTalk:Messaging|Documents received/Sec|RxHost (or name of the receive host)|*BizTalk Server Computer#n in the BizTalk Server Group*|  
|BizTalk:Messaging|Documents processed/Sec|TxHost (or name of the send host)|*BizTalk Server Computer#1 in the BizTalk Server Group*|  
|BizTalk:Messaging|Documents processed/Sec|TxHost (or name of the send host)|*BizTalk Server Computer#2 in the BizTalk Server Group*|  
|BizTalk:Messaging|Documents processed/Sec|TxHost (or name of the send host)|*BizTalk Server Computer#n in the BizTalk Server Group*|  
|Processor|% Processor Time|_Total|*BizTalk Server Computer#1 in the BizTalk Server Group*|  
|Processor|% Processor Time|_Total|*BizTalk Server Computer#2 in the BizTalk Server Group*|  
|Processor|% Processor Time|_Total|*BizTalk Server Computer#n in the BizTalk Server Group*|  
|Processor|% Processor Time|_Total|*SQL Server instance that houses the BizTalk Server databases*|