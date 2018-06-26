---
title: "Step 3: Create a Load Test to Perform Multiple Unit Tests Simultaneously | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5dd7e31-7188-4edf-9513-ea2725950b47
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Create a Load Test to Perform Multiple Unit Tests Simultaneously
Load tests run multiple instances of one or more unit tests so that you can measure your application's performance and ability to handle load. The primary components of a Visual Studio 2010 load test include:  
  
- **Scenarios** – The section of a load test where you configure the test load pattern, test mix model, test mix, network mix and Web browser mix. Scenarios accommodate the complexity of simulating complex real world work load profiles. For a comprehensive listing of all load test scenario properties see [Load Test Scenario Properties](http://go.microsoft.com/fwlink/?LinkId=208327) (http://go.microsoft.com/fwlink/?LinkId=208327).  
  
- **Counter Sets** – The section of a load test where you create particular groupings or “Sets” of performance counters to be collected while the load test is running. Several predefined counter sets are provided by default and custom counter sets can be added. For example to evaluate Network performance you can create a custom counter set, add the relevant Network performance counters and save it to the list of available counter sets. For more information about creating and saving counter sets for load tests see [Specifying the Counter Sets for Computers in a Load Test](http://go.microsoft.com/fwlink/?LinkId=208328) (http://go.microsoft.com/fwlink/?LinkId=208328).  
  
- **Run Settings** – Run settings define multiple aspects of a load test, including the test duration, the counter sets that are associated with various computers during the load test, various test validation options, and test results storage options. You can create and store multiple run settings for each load test, and then select a particular setting to use when you run the test. An initial run setting is added to your load test when you create your load test with the New Load Test Wizard. For a comprehensive listing of all load test run setting properties see [Load Test Run Setting Properties](http://go.microsoft.com/fwlink/?LinkId=208329) (http://go.microsoft.com/fwlink/?LinkId=208329).  
  
  Load tests are created using the New Load Test Wizard, edited with the Load Test Editor, and analyzed in the Load Test Analyzer. All these tools are included in Microsoft Visual Studio Ultimate edition. For more information about creating and editing load tests in Visual Studio 2010 Ultimate edition see [Creating and Editing Load Tests](http://go.microsoft.com/fwlink/?LinkId=208308) (http://go.microsoft.com/fwlink/?LinkId=208308).  
  
  Follow the steps in the sections below to add a load test to the test project described in [Step 1: Create a Unit Test to Submit Documents to BizTalk Server](../technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md). These steps also describe how to configure the **Scenarios**, **Counter Sets**, and **Run Settings** for a load test.  
  
##  <a name="BKMK_StepLoadTest"></a> Add a Load Test and Configure the Load Test Scenario, Counter Sets, and Run Settings  
 This topic describes how to use the **New Load Test Wizard** to add a load test to a test project and how to configure the load test to meet specific needs.  
  
### Use the New Load Test Wizard to Add a Load Test to the Test Project  
 Follow these steps to add a load test to a test project using the New Load Test Wizard.  
  
1.  Open the **Load Test** solution in Visual Studio 2010 if it is not already open.  
  
2.  Add a folder to the BTSLoad project; this folder will contain any load tests that are created as part of this project. In Solution Explorer, right-click the BTSLoad project, point to **Add**, and click **New Folder**. A folder icon with the highlighted text **NewFolder1** will appear under the BTSLoad project, type **LoadTests** to change the highlighted text and press the Enter key to complete creation of the folder C:\Projects\LoadTest\BTSLoad\LoadTests.  
  
3.  In Solution Explorer, right-click on the **BTSLoad** project, point to **Add**, and then click **Load Test** to start the **New Load Test Wizard**.  
  
4.  Click **Next**.  
  
5.  On the **Edit Settings for a Load Test Scenario** page under **Enter a name for the load test scenario:** type **BTS_Messaging_Step**. Under **Think time profile** select **Do not use think times** and then click **Next**.  
  
6.  On the **Edit load pattern settings for a load test scenario** page select **Step load**, enter the values below and then click **Next**.  
  
    -   **Start user count:** 30 users  
  
    -   **Step duration:** 60 seconds  
  
    -   **Step user count:** 10 users  
  
    -   **Maximum user count** 80 users  
  
    > [!NOTE]  
    >  When applying settings for a step load pattern you should calculate the amount of time required for all step increments to complete. For example, using the load pattern settings specified above the load test will need 5 minutes to complete all of the 60 second step increments when ramping up from 30 to 80 users. On the last page of the New Load Test Wizard you will be presented with options for specifying the length of the load test, one of which will be **Load Test Duration**. If you have already calculated the time required for all step increments to complete then it is a straightforward task to enter the value (5 minutes in this case) for **Load Test Duration**.  
  
7.  On the **Select a test mix model for the load test** page select **Based on the number of virtual users** and then click **Next**.  
  
8.  On the **Add tests to the load test scenario and edit the test mix** page click the **Add** button.  
  
9. Under **Available tests** double-click **BTSMessaging** and **BTSMessaging2** to add these unit tests to the list of **Selected tests**. Click **OK** and then click **Next**.  
  
10. On the **Add network types to a load test scenario and edit the network mix** page verify that **Network Type** is set to **LAN** with a **Distribution** of **100%** and then click **Next**.  
  
11. On the **Specify computers to monitor with counter sets during load test run** page click **Next**.  
  
    > [!NOTE]  
    >  Do not add computers to the load test at this time. The New Load Test Wizard will only allow you to associate computers with predefined counter sets, and this load test requires the use of both predefined and *custom* counter sets. After the wizard is complete and the load test is saved you can edit the load test to add custom counter sets and configure the load test to monitor computers using both predefined *and* custom counter sets.  
  
     On the **Review and edit run settings for a load test** page enter the following values:  
  
    1.  Select **Load test duration**.  
  
    2.  **Warm-up duration (hh mm ss)** 30 seconds  
  
    3.  **Run duration (hh mm ss)** 5 minutes  
  
        > [!NOTE]  
        >  The time allocated for **Run duration** should equal the amount of time required for all step increments to complete as described in step 5 above, or 5 minutes for this example.  
  
    4.  **Sampling rate** 5 seconds  
  
    5.  **Description** (optional), Enter a description for the load test here.  
  
    6.  **Save Log on Test Failure** True  
  
    7.  **Validation level** Low – invoke validation rules marked low  
  
12. Click **Finish** to close the New Load Test Wizard.  
  
13. Click the **File** menu and select **Save \<Load Test Name\>.loadtest As**.  
  
    > [!NOTE]  
    >  In this example, <Load Test Name> will be the name assigned to the load test file by Visual Studio 2010, typically loadtestx.loadtest, unless the name of the file has already been manually changed.  
  
14. Save the file to the C:\Projects\LoadTest\BTSLoad\LoadTests directory created earlier. It may be useful to save the file with the name used for the scenario; in this example the scenario name is BTS_Messaging_Step so the loadtest file would be saved as C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Step.loadtest.  
  
###  <a name="BKMK_BTSCounters"></a> Add a Custom Counter Set to Measure BizTalk Server Key Performance Indicators (KPI)  
 Follow these steps to add a counter set with performance counters that measure BizTalk Server KPI required for determining Maximum Sustainable Throughput (MST) of the BizTalk Server application:  
  
1. In Solution Explorer double-click the load test that you created in the previous section to view the load test in Load Test editor.  
  
2. In Load Test editor, click to expand **Counter Sets**. Notice that there is no predefined counter set for BizTalk Server, therefore a custom “BizTalk Server” counter set must be added to the list of counter sets.  
  
3. Right-click **Counter Sets** and select **Add Custom Counter Set**. By default this action will create a custom counter set with the name **Custom1**.  
  
4. Right-click the **Custom1** counter set and select **Properties** to set focus to the **Properties** dialog for the Custom1 counter set.  
  
5. Double-click the name **Custom1** in the **Properties** dialog, type **BizTalk** and then press the ENTER key to rename the custom counter set to **BizTalk**.  
  
6. In Load Test Editor, right-click the **BizTalk** counter set and select **Add Counters**.  
  
7. Under **Computer**, type the name of one of the BizTalk Server computers in the BizTalk Server group to display performance monitor categories that include BizTalk Server performance counters.  
  
   > [!IMPORTANT]
   >  To ensure that all BizTalk Server performance categories and performance counters are listed, you may need to type in the fully qualified domain name (or IP Address) of a BizTalk Server in the group and you may also need to start the instances of the following hosts on the BizTalk Server computer.  
   > 
   > - Instances of BizTalk hosts which are bound to orchestrations that will run during the load test.  
   >   -   Instances of BizTalk hosts configured as send or receive handlers for adapters that will run during the load test.  
  
8. BizTalk Server provides quite an extensive set of performance counters. For purposes of determining the Maximum Sustainable Performance (MST) of a BizTalk Server application you only need to add the following BizTalk Server performance counters to the **BizTalk** custom counter set:  
  
   |Performance Category|Performance Counter|  
   |--------------------------|-------------------------|  
   |Processor|% Processor Time for the _Total counter instance.|  
   |BizTalk:Message Box: General Counters|Spool Size for the *\<BizTalk MessageBox database name\>*:*\<SQL Server instance name\>* counter instance. **Note:**  *\<BizTalk MessageBox database name\>* and *\<SQL Server instance name\>* are just placeholders for the actual names of the BizTalk MessageBox database and the SQL Server instance that houses the BizTalk MessageBox database. These placeholders should be replaced with the actual names of the BizTalk MessageBox database and associated SQL Server instance.|  
   |BizTalk:Messaging|Documents received/Sec for the receive host counter instance.<br /><br /> Documents processed/Sec for the transmit host counter instance.|  
   |BizTalk:Message Agent|Message delivery incoming rate for the document receive host.|  
   |BizTalk:Message Agent|Message publishing outgoing rate for the document transmit host.|  
   |XLANG/s Orchestrations|Orchestrations completed/sec for the Orchestration processing host.|  
  
### Modify Run Settings to Map Counter Sets to Appropriate Computers  
 Follow these steps to map the appropriate counter sets with the appropriate computers for the load test:  
  
1.  In **Load Test Editor**, right-click **Run Settings** and select **Manage Counter Sets**.  
  
2.  Click **Add Computer** to add a new computer to the list. An icon with the highlighted text **New Computer** will appear under **Computers and counter sets to monitor**. Replace the highlighted text by typing the name of the computer you would like to add to the list.  
  
3.  After adding the computer to the list, click to expand the list of available counter sets and then click to select one or more of the available counter sets to associate the counter set(s) with the computer.  
  
4.  Repeat steps 2 and 3 until you have associated counter sets with all computers for which you would like to collect performance data.  
  
###  <a name="BKMK_TestSettings"></a> Add a Test Settings File to the Solution to Run Tests and Collect Data Remotely  
 To configure the Load test to use the Test Controller and Test Agent computers that you created in [Step 2: Configure Load Test Controller and Agent Computers](../technical-guides/step-2-configure-load-test-controller-and-agent-computers.md), follow the steps in [Add a test settings for remote execution or data collection to your solution](http://go.microsoft.com/fwlink/?LinkId=209182)(http://go.microsoft.com/fwlink/?LinkId=209182) as noted below:  
  
1.  For Step 3, enter the name **BizTalkLoadTest**  
  
2.  Ignore Step 6 because you have already entered a name in Step 3.  
  
3.  For Step 7, enter “These are default test settings for a remote test run” under **Description**.  
  
4.  For Step 8, select the default naming scheme.  
  
5.  For Step 9, under **Test execution method** select **Remote execution**, under **Controller** select the test controller computer and leave the remaining properties on the **Roles** page at their default settings.  
  
6.  For Step 24, select the option **to Run in default host**, select a **Host type** of **Default**, and under **Run tests in 32 or 64 bit process**, select the option to **Run tests in 64 bit process on 64 bit machine**.  
  
7.  For Step 25, select **Mark an individual test as failed if its execution time exceeds** and leave the default value of 30 minutes selected.  
  
8.  For Step 27b, select the check box for **Use the Load Context for assemblies in the test directory**, and then click **Save As**.  
  
9. In the **Save As** dialog box, verify that the name **BizTalkLoadTest** is entered next to **File name**, and click **Save**. You have now added a test settings file to your solution.