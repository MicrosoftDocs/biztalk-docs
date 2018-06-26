---
title: "Poll Oracle E-Business Suite using SELECT statement with the WCF channel model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 495b9010-856f-4782-bd19-1522bc3eb950
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Poll Oracle E-Business Suite using SELECT statement with the WCF channel model
You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive periodic data-change messages by using a SELECT statement to continuously poll the interface tables, interface views, tables and views in Oracle E-Business Suite. You can specify a SELECT statement as a polling statement that the adapter executes periodically to poll Oracle E-Business Suite. You can also specify a post-poll PL/SQL code block that the adapter executes after the polling statement is executed.  

 To enable polling, you must specify certain binding properties as described in this topic. For more information about how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  

## Configuring a Polling Operation with Oracle E-Business Suite Adapter Binding Properties  
 The following table summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure the adapter to receive data change messages. You must specify these binding properties while running the polling application.  


|         Binding Property         |                                                                                                                                                                                                                            Description                                                                                                                                                                                                                             |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                          Specifies whether you want to perform **Polling** or **Notification** inbound operation. Default is **Polling**.                                                                                                                                                                          |
| **PolledDataAvailableStatement** |                                                                                                             Specifies the SQL statement that the adapter executes to determine whether any data is available for polling. Only if a record is available, the SELECT statement you specify for the **PollingInput** binding property will be executed.                                                                                                              |
|       **PollingInterval**        | Specifies the interval, in seconds, at which the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property. The default is 30 seconds. The polling interval determines the time interval between successive polls. If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval. |
|         **PollingInput**         |                         Specifies the polling statement. To poll using a SELECT statement, you must specify a SELECT statement for this binding property. The default is null.<br /><br /> You must specify a value for **PollingInput** binding property to enable polling. The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.                          |
|        **PollingAction**         |                                                                                                                Specifies the action for the polling operation. You can determine the polling action from the service interface generated for the operation using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].                                                                                                                |
|      **PostPollStatement**       |                                                                                                                                                                  Specifies a statement block that is executed after the statement specified by the **PollingInput** binding property is executed.                                                                                                                                                                  |
|      **PollWhileDataFound**      |                                    Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled. If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval. Default is false.                                     |

 For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database, read the remainder of this topic.  

## How This Topic Demonstrates Polling  
 In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving data change messages using SELECT statements, you poll the **MS_SAMPLE_EMPLOYEE** interface table in the **Application Object Library** application. This table is created when you run the create_apps_artifacts.sql script provided with the samples to create these objects in Oracle E-Business Suite.  

 To demonstrate a polling operation, we do the following:  

-   Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the interface table being polled (MS_SAMPLE_EMPLOYEE) has any data. In this example, you can set this binding property as:  

    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  

     This ensures that the adapter executes the polling statement only when the MS_SAMPLE_EMPLOYEE interface table has some records.  

-   Specify a SELECT statement for the **PollingInput** binding property. This statement retrieves all the rows in the MS_SAMPLE_EMPLOYEE interface table. In this example, you can set this binding property as:  

    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  

    > [!NOTE]
    >  For information about the FOR UPDATE clause used in the SELECT statement, see [Receive polling-based data-changed messages from Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md).  

-   Specify a DELETE statement as part of the **PostPollStatement** binding property. This statement will delete all data from MS_SAMPLE_EMPLOYEE interface table. In this example, you can set this binding property as:  

    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  

     After this happens, the next time the statement specified for **PollingInput** will be executed, it will not fetch any data.  

-   Until more data is added to the MS_SAMPLE_EMPLOYEE interface table, you will not get any polling messages so you must repopulate the MS_SAMPLE_EMPLOYEE interface table with new records. You can do so by running the insert_apps_data.sql script provided with the samples. After you run this script, the next polling operation will fetch the new records inserted into the table.  

## Consuming the Polling Request Message  
 The adapter invokes the polling operation on your code to poll the Oracle E-Business Suite. That is, the adapter sends a polling request message that you receive over an IInputChannel channel shape. The polling request message contains the result set of the query specified by the **PollingInput** binding property. You can consume the polling message in one of two ways:  

-   To consume the message using node-value streaming, you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.  

-   To consume the message using node streaming, you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.  

## About the Examples Used in this Topic  
 The examples in this topic poll the MS_SAMPLE_EMPLOYEE interface table. A script to generate the table is supplied with the samples. For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md). A sample, **SelectPolling_ChannelModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.  

## Receiving Inbound Messages for Polling Operation Using the WCF Channel Model  
 This section provides instructions on how to write a .NET application (channel model) to receive inbound polling messages using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  

#### To receive polling messages from the adapter  

1. Create a Microsoft Visual C#® project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. For this topic, create a console application.  

2. In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.  

3. Open the Program.cs file and add the following namespaces:  

   -   `Microsoft.Adapters.OracleEBS`  

   -   `System.ServiceModel`  

   -   `System.ServiceModel.Description`  

   -   `System.ServiceModel.Channels`  

   -   `System.Xml`  

4. Specify a connection URI. For more information about the adapter connection URI, see [Create the Oracle E-Business Suite connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).  

   ```  
   Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
   ```  

5. Create an instance of **OracleEBSBinding** and set the binding properties required to configure polling. At a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, and **PollingAction** binding properties. For more information about binding properties used to configure polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  

   ```  
   OracleEBSBinding binding = new OracleEBSBinding();  
   binding.InboundOperationType = InboundOperation.Polling;  
   binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
   binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
   binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
   binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
   ```  

6. Because you are polling an interface table, you must also set the applications context. For more information about application context and binding properties required for setting application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  

   ```  
   binding.OracleUserName = "<Enter user name here>";  
   binding.OraclePassword = "<Enter password here>";  
   binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  
   ```  

7. Create a binding parameter collection and set the credentials.  

   ```  
   ClientCredentials credentials = new ClientCredentials();  
   credentials.UserName.UserName = "<Enter user name here>";  
   credentials.UserName.Password = "<Enter password here>";  

   BindingParameterCollection bindingParams = new BindingParameterCollection();  
   bindingParams.Add(credentials);  
   ```  

8. Create a channel listener and open it. You create the listener by invoking **BuildChannelListener<IInputChannel\>** method on the **OracleEBSBinding**.  

   ```  
   IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
   listener.Open();  
   ```  

9. Get an **IInputChannel** channel by invoking the **AcceptChannel** method on the listener and open it.  

    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  

10. Invoke **Receive** on the channel to get the next inbound message from the adapter.  

    ```  
    Message message = channel.Receive();  
    ```  

11. Consume the result set returned by the inbound operation. You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.  

    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  

12. Close the channel when you have completed processing the request.  

    ```  
    channel.Close()  
    ```  

    > [!IMPORTANT]
    >  You must close the channel after you have finished processing the inbound operation. Failure to close the channel may affect the behavior of your code.  

13. Close the listener when you are finished receiving data-changed messages.  

    ```  
    listener.Close()  
    ```  

    > [!IMPORTANT]
    >  Closing the listener does not close channels created using the listener. You must explicitly close each channel created using the listener.  

### Example  
 The following example shows a polling application that polls the MS_SAMPLE_EMPLOYEE interface table. The **PollingInput** property contains the select statement that reads all the data from the MS_SAMPLE_EMPLOYEE table and the post poll statement deletes all the data from the same table. The polling message is written to `C:\PollingOutput.xml`.  

 Subsequent polling messages will not contain any records until more data is added to the MS_SAMPLE_EMPLOYEE interface table. You can do so by running the insert_apps_data.sql script provided with the samples. After you run this script, the next polling operation will fetch the new records inserted into the table. The adapter will continue to poll until you close the service host by pressing \<RETURN\>.  

```  
using System;  
using Microsoft.Adapters.OracleEBS;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Xml;  

namespace SelectPolling_ChannelModel  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("Sample started. This sample will poll 5 times and will perform the following tasks:");  
            Console.WriteLine("Press any key to start polling...");  
            Console.ReadLine();  
            IChannelListener<IInputChannel> listener = null;  

            IInputChannel channel = null;  

            try  
            {  
                TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  

                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
                binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
                binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
                binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
                binding.OracleUserName = "<Enter user name here>";  
                binding.OraclePassword = "<Enter password here>";  
                binding.OracleEBSResponsibilityName = "<Enter responsibility here>";  

                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name?");  

                ClientCredentials credentials = new ClientCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  

                BindingParameterCollection bindingParams = new BindingParameterCollection();  
                bindingParams.Add(credentials);  

                listener = binding.BuildChannelListener<IInputChannel>(ConnectionUri, bindingParams);  
                listener.Open();  

                channel = listener.AcceptChannel();  
                channel.Open();  

                Console.WriteLine("Channel and Listener opened...");  
                Console.WriteLine("\nWaiting for polled data...");  
                Console.WriteLine("Receive request timeout is {0}", messageTimeout);  

                // Poll five times with the specified message timeout   
                // If a timeout occurs polling will be aborted  
                for (int i = 0; i < 5; i++)  
                {  
                    Console.WriteLine("Polling: " + i);  
                    Message message = null;  
                    XmlReader reader = null;  
                    try  
                    {  
                        //Message is received so process the results  
                        message = channel.Receive(messageTimeout);  
                    }  
                    catch (System.TimeoutException toEx)  
                    {  
                        Console.WriteLine("\nNo data for request number {0}: {1}", i + 1, toEx.Message);  
                        continue;  
                    }  

                    // Get the query results using an XML reader  
                    try  
                    {  
                        reader = message.GetReaderAtBodyContents();  
                    }  
                    catch (Exception ex)  
                    {  
                        Console.WriteLine("Exception :" + ex);  
                        throw;                          
                    }  

                    XmlDocument doc = new XmlDocument();  
                    doc.Load(reader);  
                    using (XmlWriter writer = XmlWriter.Create("C:\\PollingOutput.xml"))  
                    {  
                        doc.WriteTo(writer);  
                        Console.WriteLine("The polling response is saved at 'C:\\PollingOutput.xml'");  
                    }  
                    // return the cursor  
                    Console.WriteLine();  

                    // close the reader  
                    reader.Close();  

                    message.Close();  
                }  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                Console.ReadLine();  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: close the channel and listener to stop polling  
                if (channel != null)  
                {  
                    if (channel.State == CommunicationState.Opened)  
                        channel.Close();  
                    else  
                        channel.Abort();  
                }  

                if (listener != null)  
                {  
                    if (listener.State == CommunicationState.Opened)  
                        listener.Close();  
                    else  
                        listener.Abort();  
                }  
            }  
        }  
    }  
}  

```  

## See Also  
 [Develop Oracle E-Business Suite applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)