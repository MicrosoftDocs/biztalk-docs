---
title: "Step 4: Configure BizTalk Server Environment for Load Testing | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f336c5f-5a18-493d-8fc0-a8a475ab47b3
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Configure BizTalk Server Environment for Load Testing
This topic provides information for creating the BizTalk Server Receive Locations, Receive Ports, and Send Ports required to run the sample code described in the topics [Step 1: Create a Unit Test to Submit Documents to BizTalk Server](~/technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md) and [Step 3: Create a Load Test to Perform Multiple Unit Tests Simultaneously](~/technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md).  

## Configure BizTalk Server Environment for Load Tests  
 As described in the topic [Step 3: Create a Load Test to Perform Multiple Unit Tests Simultaneously](~/technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md), the load test **BTS_Messaging_Step** is configured to execute the unit tests **BTSMessaging** and **BTSMessaging2**. In turn, these unit tests load a copy of the message C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml and send it to the endpoints **BTSMessagingEP** and **BTSMessagingEP2** as defined in the following section of the project’s application configuration (app.config) file:  

 \<\!-- BTSMessagingEP --\>         \<endpoint address="net.tcp://*BizTalk Server Computer*:8123/btsloadtest" binding="netTcpBinding" bindingConfiguration="netTcpBinding" contract="System.ServiceModel.Channels.IRequestChannel" name="BTSMessagingEP" /\>         \<endpoint address="net.tcp://*BizTalk Server Computer*:8123/btsloadtest" binding="netTcpBinding" bindingConfiguration="netTcpBinding" contract="System.ServiceModel.Channels.IRequestChannel" name="BTSMessagingEP2" /\>  

> [!NOTE]
>  As noted earlier, *BizTalk Server Computer* is a placeholder for the actual BizTalk Server computer names or, in the case that the BizTalk Server Computers are configured as members of a Network Load Balancing (NLB) cluster; *BizTalk Server Computer* is a placeholder for the name or address of the corresponding NLB virtual server.  

 For purposes of this example, two BizTalk Server computers were used and the BizTalk Server Message Box database was on a remote SQL Server computer.  

### Create BizTalk Server Send and Receive Hosts  
 Follow the steps in the BizTalk Server Documentation topic [How to Create a New Host](http://go.microsoft.com/fwlink/?LinkId=208595) (http://go.microsoft.com/fwlink/?LinkId=208595) to create a BizTalk Server “Send” host for Send Ports and Send adapter handlers. Configure the host with the following properties:  

|Property|Value|  
|--------------|-----------|  
|Name|TxHost|  
|Type|In-Process|  
|Allow Host Tracking|Ensure that this box is un-checked.|  
|Authentication Trusted|Ensure that this box is un-checked.|  
|32-bit only|Ensure that this box is un-checked.|  
|Make this the default host in the group|Ensure that this box is un-checked.|  
|Windows group|The Windows group used to control access to this host and associated host instances. The Window group created for the default in-process host is named either *\<Computer Name\>*\BizTalk Application Users (for a single server BizTalk Server installation) or *\<Domain Name\>*\BizTalk Application Users (for a multiple server BizTalk Server installation, which requires the use of domain groups). **Note:**  *\<Computer Name\>* and *\<Domain Name\>* are placeholders for the actual computer name or domain name used when the group was created. <br /><br /> If a new group is created for this host then it must have the privileges described in the topic [Host Groups](http://go.microsoft.com/fwlink/?LinkId=208803) (http://go.microsoft.com/fwlink/?LinkId=208803) in the BizTalk Server documentation.|  

 Repeat the steps that you followed when creating the “Send” host to create a “Receive” host. Configure the “Receive” host with the following property values:  

|Property|Value|  
|--------------|-----------|  
|Name|RxHost|  
|Type|In-Process|  
|Allow Host Tracking|Ensure that this box is un-checked.|  
|Authentication Trusted|Ensure that this box is un-checked.|  
|32-bit only|Ensure that this box is un-checked.|  
|Make this the default host in the group|Ensure that this box is un-checked.|  
|Windows group|The Windows group used to control access to this host and associated host instances. The Window group created for the default in-process host is named either *\<Computer Name\>*\BizTalk Application Users (for a single server BizTalk Server installation) or *\<Domain Name\>*\BizTalk Application Users (for a multiple server BizTalk Server installation, which requires the use of domain groups). **Note:**  *\<Computer Name\>* and *\<Domain Name\>* are placeholders for the actual computer name or domain name used when the group was created. <br /><br /> If a new group is created for this host then it must have the privileges described in the topic [Host Groups](http://go.microsoft.com/fwlink/?LinkId=208803) (http://go.microsoft.com/fwlink/?LinkId=208803) in the BizTalk Server documentation.|  

### Create Instances of the BizTalk Server Send and Receive Hosts  
 Follow the steps in the BizTalk Server Documentation topic [How to Add a Host Instance](http://go.microsoft.com/fwlink/?LinkId=208596) (http://go.microsoft.com/fwlink/?LinkId=208596) to create and start instances of the BizTalk Server “Send” host. Configure an instance of the “Send” host to run on each BizTalk Server in the BizTalk Server group and configure each host instance with the following property values:  

|Property|Value|  
|--------------|-----------|  
|**Host name**|Select **TxHost** from the drop-down list next to **Host name**.|  
|**Server**|Select the BizTalk Server that will run this host instance from the drop-down list next to **Server**.|  
|**Logon**|1.  Click the **Configure** button to display the **Logon Credentials** dialog box.<br />2.  In the **Logon Credentials** dialog box enter the following values for the specified properties:<br />     **Property**<br />     **Logon**: Name of user account that is a member of the Windows group associated with this BizTalk Server host.<br />     **Password**: Password for the user account specified in the **Logon** textbox.<br />3.  Click **OK** to close the **Logon Credentials** dialog box.|  
|**Disable host instance from starting.**|Ensure that this box is un-checked.|  

 After creating the host instance, right-click on the host instance and select **Start** from the context menu.  

 Repeat the steps that you followed when creating the “Send” host instances to create “Receive” host instances. Configure an instance of the “Receive” host to run on each BizTalk Server in the BizTalk Server group and configure each host instance with the following property values:  

|Property|Value|  
|--------------|-----------|  
|Host name|Select **RxHost** from the drop-down list next to **Host name**.|  
|Server|Select the BizTalk Server that will run this host instance from the drop-down list next to **Server**.|  
|Logon|1.  Click the **Configure** button to display the **Logon Credentials** dialog box.<br />2.  In the **Logon Credentials** dialog box enter the following values for the specified properties:<br />     **Property**<br />     **Logon**: Name of user account that is a member of the Windows group associated with this BizTalk Server host.<br />     **Password**: Password for the user account specified in the **Logon** textbox.<br />3.  Click **OK** to close the Logon Credentials dialog box.|  
|Disable host instance from starting|Ensure that this box is un-checked.|  

 After creating the host instance, right-click on the host instance and select **Start** from the context menu.  

### Create a BizTalk Server Receive Port  
 Follow the steps in the topic [How to Create a Receive Port](http://go.microsoft.com/fwlink/?LinkID=154843) (http://go.microsoft.com/fwlink/?LinkID=154843) in the BizTalk Server documentation to create a One-Way Receive Port. When creating the Receive port, leave all properties at default values except as noted in the table below:  

|Property|Value|  
|--------------|-----------|  
|General\Name|BTSLoadTestMessaging.OneWay.ReceivePort|  
|General\Port Type|One-Way|  
|General\Authentication|No authentication|  
|General\Enable routing for failed messages|Ensure that this box is un-checked.|  
|General\Description|Leave blank|  
|Inbound Maps|None|  
|Tracking|Ensure that all boxes are un-checked.|  
|Receive Locations|Click **New**, this will display the **Receive Location Properties** dialog box which should be configured as described in the following section, **Create a BizTalk Server Receive Location**.|  

### Create a BizTalk Server Receive Location  
 In the **Receive Location Properties** dialog box displayed while creating the BizTalk Server Receive port, apply the specified property values:  

|Property|Value|  
|--------------|-----------|  
|Name:|BTSLoadTest.Messaging.OneWay.WCF-Customer.ReceiveLocation|  
|Receive handler:|RxHost|  
|Receive pipeline:|PassThruReceive|  
|Description:|Leave this blank|  
|Type:|Select **WCF-Custom** from the drop-down list and then click the **Configure** button, this will display the **WCF-Custom Transport Properties** dialog box which should be configured as described in the following section, **Configure the WCF-Custom Receive Transport**.|  

### Configure the WCF-Custom Receive Transport  
 In the **WCF-Custom Transport Properties** dialog box displayed while creating the BizTalk Server Receive location, leave all properties at default values except as noted in the table below:  

|Property|Value|  
|--------------|-----------|  
|General\Address (URI)|net.tcp://localhost:8123/btsloadtest|  
|Binding\Binding Type|netTcpbinding|  
|Binding\NetTcpBindingElement\listenBacklog|400|  
|Binding\NetTcpBindingElement\maxConnections|400|  
|Binding\Security\NetTcpSecurityElement\mode|None|  
|Behavior\ServiceBehavior\serviceThrottling\ServiceThrottlingElement **Note:**  To add the serviceThrottling behavior to the list of behaviors, right-click ServiceBehavior, click **Add Extension**, select **serviceThrottling** from the list of behavior extensions and then click **OK**.|Set the **ServiceThrottlingElement** properties to the following values:<br /><br /> -   **maxConcurrentCalls** 400<br />-   **maxConcurrentInstances** 400<br />-   **maxConcurrentSessions** 400|  
|Behavior\ServiceBehavior\serviceDebug\ServiceDebugElement **Note:**  To add the serviceDebug behavior to the list of behaviors, right-click ServiceBehavior, click **Add Extension**, select **serviceDebug** from the list of behavior extensions, and then click **OK**.|Leave the list of **ServiceDebugElement** properties at their default values (empty) except for the following properties, which should be changed to a value of True:<br /><br /> -   **httpHelpPageEnabled** True<br />-   **httpsHelpPageEnabled** True<br />-   **includeExceptionDetailInFaults** True|  

 Click **OK** to close the WCF-Custom Transport Properties dialog box and then click **OK** again to close the Receive Location Properties dialog box.  

### Create a BizTalk Server Send Port  
 Follow the steps in the topic [How to Create a Send Port](http://go.microsoft.com/fwlink/?LinkID=154845) (http://go.microsoft.com/fwlink/?LinkID=154845) in the BizTalk Server documentation to create a **Static One-Way** Send Port. When creating the Send port, leave all properties at default values except as noted in the table below:  

|Property|Value|  
|--------------|-----------|  
|General\Name|BTSLoadTest.Messaging.Send.WCF-Custom|  
|General\Send handler|TxHost|  
|General\Send pipeline|PassThruTransmit|  
|Filters\Name|BTS.ReceivePortName|  
|Filters\Operator|==|  
|Filters\Value|BTSLoadTest.Messaging.OneWay.ReceivePort|  
|Filters\Group by|And **Note:**  If these properties are configured with the correct values, the filter should be displayed as                                              `BTS.ReceivePortName == BTSLoadTest.Messaging.OneWay.ReceivePort` as seen toward the bottom of the Filters page of the Send Port Properties dialog box. As a result of applying this filter, this Send port subscribes to any messages received by BizTalk Server via the Receive Port named BTSLoadTest.Messaging.OneWay.ReceivePort.|  
|Tracking|Ensure that all boxes are un-checked.|  
|General\Type|Select **WCF-Custom** from the drop-down list and then click the **Configure** button, this will display the **WCF-Custom Transport Properties** dialog box which should be configured as described in the following section, **Configure the WCF-Custom Send Transport**.|  

### Configure the WCF-Custom Send Transport  
 In the **WCF-Custom Transport Properties** dialog box displayed while creating the BizTalk Server Send Port, leave all properties at default values except as noted in the table below:  

|Property|Value|  
|--------------|-----------|  
|General\Address (URI)|net.tcp://*\<Computer Name\>*:2001/TCP1 **Important:**  *\<Computer Name\>* is a placeholder for the actual computer name used to host IndigoService.exe, which is designed to consume messages sent via WCF. Because IndigoService.exe requires very little resources, it is often perfectly acceptable to run IndigoService.exe on the SQL Server computer used for the BizTalk Server group databases. IndigoService.exe is part of the BizTalk Benchmark Wizard, which is available at [BizTalk Benchmark Wizard](http://go.microsoft.com/fwlink/?LinkID=186347) (http://go.microsoft.com/fwlink/?LinkID=186347).|  
|Binding\Binding Type|**customBinding**|  

 As with most of the WCF-Custom Binding Types, the **customBinding** Binding type exposes several properties, which should be set to the following values:  

1.  Under the **Binding** section there is a **CustomBindingElement** property with an associated **Configuration** section. Leave all of the values in the Configuration section for the **CustomBindingElement** property at their default values.  

2.  Then under **CustomBindingElement** right-click **textMessageEncoding** and select **Remove extension (Del)**. Likewise, right-click **httpTransport** and select **Remove extension (Del)**.  

3.  Now right-click **CustomBindingElement** and select **Add extension Ins** to display the **Select Binding Element Extension** dialog box.  

4.  Select **binaryMessageEncoding** and click **OK** to add the **binaryMessageEncoding** element extension. Repeat the steps to display the **Select Binding Element Extension** dialog box and scroll down the list of available element extensions until you see the **tcpTransport** element extension, select **tcpTransport** and click **OK**.  

5.  Under **CustomBindingElement** select the **tcpTransport** element and in the Configuration section for **tcpTransport**, leave all properties at default values except as noted in the following table:  

    |Property|Value|  
    |--------------|-----------|  
    |connectionBufferSize|2097152|  
    |maxBufferSize|2097152|  
    |maxPendingAccepts|400|  
    |maxPendingConnections|400|  
    |listenBacklog|400|  
    |maxBufferPoolSize|2097152|  
    |maxReceivedMessageSize|2097152|  

6.  Under the **tcpTransport** element select the **ConnectionPoolSettings** element and leave all properties at default values except for the **maxOutboundConnectionsPerEndpoint** property, which should be changed to a value of 400.  

7.  Click **OK** to close the WCF-Custom Transport Properties dialog box, then click **OK** again to close the BTSLoadTest.Messaging.Send.WCF-Custom – Send Port Properties dialog box.  

### Configure a Computer to Consume Messages Sent by the BizTalk Server Send Port  
 As described earlier, the IndigoService.exe is designed to consume messages sent via WCF. IndigoService.exe is part of the BizTalk Benchmark Wizard, which is available at [BizTalk Benchmark Wizard](http://go.microsoft.com/fwlink/?LinkID=186347) (http://go.microsoft.com/fwlink/?LinkID=186347). The easiest way to set up and run IndigoService.exe for purposes of this example is to simply download the BizTalk Benchmark Wizard zip file from the [BizTalk BenchMark Wizard download page](http://go.microsoft.com/fwlink/?LinkID=209100) (http://go.microsoft.com/fwlink/?LinkID=209100) and extract the following 4 files onto the computer that you would like to run IndigoService.exe:  

1. \IndigoService\bin\Release\IndigoService.exe  

2. \IndigoService\bin\Release\IndigoService.exe.config  

3. \IndigoService\bin\Release\Response.xml  

4. \IndigoService\bin\Release\StartIndigoService.bat  

   Then, start IndigoService.exe by double-clicking on StartIndigoService.bat. IndigoService.exe consumes messages sent to the endpoint specified in the IndigoService.exe.config file:  

   \<endpoint address="net.tcp://localhost:2001/TCP1"             binding="netTcpBinding"             bindingConfiguration="Binding1"             name="endpoint1"             contract="IndigoService.IServiceTwoWaysVoidNonTransactional" /\>  

   This is why the Send Port Address is configured with an Address (URI) of net.tcp://*\<Computer Name\>*:2001/TCP1  

   Because IndigoService.exe requires very little resources, it is often perfectly acceptable to run IndigoService.exe on the SQL Server computer used for the BizTalk Server databases.  

### Disable Tracking and Throttling for the BizTalk Server Group  
 In order to determine the absolute maximum sustainable throughput of the system, both message Tracking and Throttling should be disabled before beginning load testing. This can be done using the BizTalk Server Administration console by following these steps:  

1. Launch the BizTalk Server Administration console. Click **Start**, point to **All Programs**, point to **BizTalk Server 2010** and then click **BizTalk Server Administration**.  

2. Under **BizTalk Server Administration**, select your BizTalk Group if it is listed or if it is not listed, right-click **BizTalk Server Administration**, select **Connect to Existing Group**, enter the SQL Server name that houses the BizTalk Group’s BizTalk Server Management database next to **SQL Server name:**, enter the name of the BizTalk Group’s management database name next to **Database name:** and then click **OK**.  

3. Right-click the BizTalk Group node and select **Settings** to display the **BizTalk Settings Dashboard**.  

4. Click to select **Hosts** in the left hand pane of the BizTalk Settings Dashboard.  

5. Click the dropdown list next to **Host** to select one of the hosts that will be used during performance testing.  

6. Leave properties at their default values except as noted in the following table:  


   |                          Property                          |               Value                |
   |------------------------------------------------------------|------------------------------------|
   |          **General\Move tracking data to DTA DB**          | Uncheck this box if it is checked. |
   |                  **General\32-bit only**                   | Uncheck this box if it is checked. |
   |          **General\Polling Intervals\Messaging**           |     Set to a value of 20000000     |
   |        **General\Polling Intervals\Orchestrations**        |     Set to a value of 20000000     |
   |     **Resource-Based Throttling\In-process messages**      |      Set to a value of 10000       |
   | **Resource-Based Throttling\Internal message queue size**  |      Set to a value of 10000       |
   |     **Resource-Based Throttling\Message count in DB**      |        Set to a value of 0         |
   | **Resource-Based Throttling\Memory Usage\Process virtual** |        Set to a value of 0         |
   |  **Rate-Based Throttling\Publishing\Throttling override**  |       Set to Do Not Throttle       |
   |   **Rate-Based Throttling\Delivery\Throttling override**   |       Set to Do Not Throttle       |


7. Repeat the process outlined in step 6 for every host that will be used during the course of performance testing.  

8. Click to select **Host Instances** in the left hand pane of the BizTalk Settings Dashboard.  

9. Click the dropdown list next to **Host Instance:** to select one of the host instances that will be used for performance testing.  

10. Leave property values at their default setting except change the **.NET CLR Maximum worker threads** to a value of **100** and change the **.NET CLR Minimum worker threads** to a value of **25**.  

11. Repeat the process outlined in step 10 for every host instance that will be used during the course of performance testing.  

    Even though disabling Tracking and Throttling does not in any way represent what should be done in a production scenario, because these operations are so expensive from a performance perspective it makes sense to disable them to find out the true Maximum Sustainable Throughput (MST) of a BizTalk Server Environment. This allows testers to clearly see the impact of any performance tweaking that has been applied to the environment. Certainly an argument could be made that tracking should not be disabled and if you know from the outset that your BizTalk Server application will require tracking then you should enable tracking. With that said, **every effort should be made to disable throttling for purposes of performance testing**. Throttling is very useful for preventing a BizTalk Server from “falling over” due to excessive load in a production environment. However, you don’t want throttling enabled during performance testing because it is expensive from a performance standpoint and because if throttling kicks in during a load test then you will have a very difficult time determining what level of performance your BizTalk Server application can actually achieve. The next topics describe how to perform step load testing to push your BizTalk Server environment beyond MST and then scale back to actual MST with constant load testing. If throttling is enabled then it will become nearly impossible to push your BizTalk environment beyond MST so that you could in turn discover what the true MST is.