---
description: "Learn more about: Step 6: Perform Constant Load Pattern Tests to Verify Maximum Sustainable Throughput"
title: "Step 6: Perform Constant Load Pattern Tests to Verify Maximum Sustainable Throughput"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 6: Perform Constant Load Pattern Tests to Verify Maximum Sustainable Throughput
When load testing a BizTalk Server solution using Visual Studio 2010, a constant load pattern test should be performed once the approximate Maximum Sustainable Throughput (MST) of the solution is determined as described in [Step 5: Perform Step Load Pattern Tests to Determine Maximum Sustainable Throughput](../technical-guides/step-5-complete-step-load-tests-to-determine-maximum-sustainable-throughput.md). This should be done to confirm that the MST is in fact sustainable over time and also so as to create a baseline load test moving forward to evaluate the effects of any performance tuning applied to the BizTalk Server application or environment.  
  
## Create and run a Constant Load Pattern Test  
 The easiest way to create a Constant Load Pattern test that uses the same Test Mix, Counter Sets, and Counter Set Mappings used by the Step Load Pattern test is to simply save the Step Load Pattern test “BTS_Messaging_Step.loadtest” as “BTS_Messaging_Constant.loadtest” and then make some changes to “BTS_Messaging_Constant.loadtest”. Follow these steps to create a Constant Load Pattern test that is based upon the existing Step Load Pattern test:  
  
1.  Open BTS_Messaging_Step.loadtest if it is not already open.  
  
2.  Click **File** and select **Save LoadTests\BTS_Messaging_Step.loadtest As**.  
  
3.  In the **Save File As** dialog box, next to **File name**, enter C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Constant.loadtest and then click **Save**.  
  
4.  In the Load Test Editor, rename the scenario **BTS_Messaging_Step** to **BTS_Messaging_Constant**. The scenario name is displayed directly under the **Scenarios** folder.  
  
5.  Leave the values for **Test Mix** and **Network Mix** unchanged but click to select **Step Load Pattern**.  
  
6.  Right-click **Step Load Pattern** and select **Properties**.  
  
7.  In the **Properties** section, under **Load Pattern** click the dropdown list next to **Pattern** and change the Pattern from **Step** to **Constant**.  
  
8.  In the **Properties** section, under **Parameters**, change the value for **Constant User Count** to a value slightly less than the number of users at which the Step Load Pattern test was becoming unsustainable (i.e. the value for the **BizTalk:Messaging\Documents received per/Sec** began to consistently exceed the value for **BizTalk:Messaging\Documents processed/Sec** and the value of the **BizTalk:Message Box:General Counters\Spool Size** began to increase unbounded).  
  
9. Under the **Run Settings** folder, right-click **Run Setting1 [Active]** and select **Properties**.  
  
10. Scroll down the list of properties to the **Timing** section and enter a value for **Run Duration** of at least 10 minutes (00:10:00) and verify that the value for **Sample Rate** is still set to 5 seconds (00:00:05).  
  
11. Start the load test by right-clicking the test name (e.g. BTS_Messaging_Constant) and then click the **Run Test** menu option.
