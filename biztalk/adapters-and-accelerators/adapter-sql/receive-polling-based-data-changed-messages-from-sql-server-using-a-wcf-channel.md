---
title: "Receive Polling-based Data-changed Messages from SQL Server by Using the WCF Channel Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0f4af71-fb0c-433d-ba74-48ee6487eb1a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Polling-based Data-changed Messages from SQL Server by Using the WCF Channel Model
You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive periodic data-change messages for SQL Server tables or views. You can specify a polling statement that the adapter executes to poll the database. The polling statement can be a SELECT statement or a stored procedure that returns a result set.  

 For more information on how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  

> [!IMPORTANT]
>  If you want to have more than one polling operation in a single application, you must specify an **InboundID** connection property as part of the connection URI to make it unique. The inbound ID you specify is added to the operation namespace to make it unique.  

## How This Topic Demonstrates Polling  
 In this topic, to demonstrate how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports receiving data change messages, create a .NET application for the **Polling** operation. For this topic, specify the **PolledDataAvailableStatement** as:  

```  
SELECT COUNT(*) FROM Employee  
```  

 The **PolledDataAvailableStatement** must return a result set with the first cell containing a positive value. If the first cell does not contain a positive value, the adapter does not execute the polling statement.  

 As part of the polling statement, perform the following operations:  

1. Select all the rows from the Employee table.  

2. Execute a stored procedure (MOVE_EMP_DATA) to move all the records from the Employee table to an EmployeeHistory table.  

3. Execute a stored procedure (ADD_EMP_DETAILS) to add a new record to the Employee table. This procedure takes the employee name, designation, and salary as parameters.  

   To perform these operations, you must specify the following for the **PollingStatement** binding property:  

```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  

 After the polling statement is executed, all the records from the Employee table are selected and the message from SQL Server is received. Once the MOVE_EMP_DATA stored procedure is executed by the adapter, all the records are moved to the EmployeeHistory table. Then, the ADD_EMP_DETAILS stored procedure is executed to add a new record to the Employee table. The next polling execution will only return a single record. This cycle continues until you close the channel listener.  

## Configuring a Polling Query with the SQL Adapter Binding Properties  
 The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure the adapter to receive data-change messages. You must specify these binding properties as part of the .NET application for polling.  


|         Binding Property         |                                                                                                                                                                                                                                         Description                                                                                                                                                                                                                                          |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                             Specifies whether you want to perform **Polling**, **TypedPolling**, or **Notification** inbound operation. Default is **Polling**.                                                                                                                                                                              |
| **PolledDataAvailableStatement** |                                                                                       Specifies the SQL statement that the adapter executes to determine whether any data is available for polling. The SQL statement must return a result set consisting of rows and columns. Only if a row is available, the SQL statement specified for the **PollingStatement** binding property will be executed.                                                                                       |
|   **PollingIntervalInSeconds**   |                         Specifies the interval, in seconds, at which the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property. The default is 30 seconds. The polling interval determines the time interval between successive polls. If the statement is executed within the specified interval, the adapter waits for the remaining time in the interval.                          |
|       **PollingStatement**       | Specifies the SQL statement to poll the SQL Server database table. You can specify a simple SELECT statement or a stored procedure for the polling statement. The default is null. You must specify a value for **PollingStatement** to enable polling. The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property. You can specify any number of SQL statements separated by a semi-colon. |
|      **PollWhileDataFound**      |                            Specifies whether the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignores the polling interval and continuously executes the SQL statement specified for the **PolledDataAvailableStatement** binding property, if data is available in the table being polled. If no data is available in the table, the adapter reverts to execute the SQL statement at the specified polling interval. Default is **false**.                             |

 For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll SQL Server, read the remainder of this topic.  

## Consuming the Polling Request Message  
 The adapter invokes the **Polling** operation on your code to poll the SQL Server database. That is, the adapter sends a Polling request message that you receive over an IInputChannel channel shape. The Polling request message contains the result set of the query specified by the PollingStatement binding property. You can consume the Polling message in one of two ways:  

-   To consume the message using node-value streaming you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.  

-   To consume the message using node streaming you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.  

## About the Examples Used in this Topic  
 The examples in this topic poll the Employee table. The example also uses the MOVE_EMP_DATA and ADD_EMP_DETAILS stored procedure. A script to generate these artifacts is supplied with the samples. For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md). A sample, **Polling_ChannelModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.  

## Receiving Inbound Messages for Polling Operation Using the WCF Channel Model  
 This section provides instructions on how to write a .NET application (channel model) to receive inbound polling messages using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

#### To receive polling messages from the SQL adapter  

1. Create a Microsoft Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. For this topic, create a console application.  

2. In the Solution Explorer, add reference to `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.  

3. Open the Program.cs file and add the following namespaces:  

   -   `Microsoft.Adapters.Sql`  

   -   `System.ServiceModel`  

   -   `System.ServiceModel.Description`  

   -   `System.ServiceModel.Channels`  

   -   `System.Xml`  

4. Specify a connection URI. For more information about the adapter connection URI, see [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  

   ```  
   Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
   ```  

5. Create an instance of **SqlAdapterBinding** and set the binding properties required to configure polling. At a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, and **PollingStatement** binding properties. For more information about binding properties used to configure polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  

   ```  
   SqlAdapterBinding binding = new SqlAdapterBinding();  
   binding.InboundOperationType = InboundOperation.Polling;  
   binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
   binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
   ```  

6. Create a binding parameter collection and set the credentials.  

   ```  
   ClientCredentials credentials = new ClientCredentials();  
   credentials.UserName.UserName = "<Enter user name here>";  
   credentials.UserName.Password = "<Enter password here>";  

   BindingParameterCollection bindingParams = new BindingParameterCollection();  
   bindingParams.Add(credentials);  
   ```  

7. Create a channel listener and open it. You create the listener by invoking **BuildChannelListener<IInputChannel\>** method on the **SqlAdapterBinding**.  

   ```  
   IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
   listener.Open();  
   ```  

8. Get an **IInputChannel** channel by invoking the **AcceptChannel** method on the listener and open it.  

   ```  
   IInputChannel channel = listener.AcceptChannel();  
   channel.Open();  
   ```  

9. Invoke **Receive** on the channel to get the next POLLINGSTMT message from the adapter.  

    ```  
    Message message = channel.Receive();  
    ```  

10. Consume the result set returned by the POLLINGSTMT operation. You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.  

    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  

11. Close the channel when you have completed processing the request.  

    ```  
    channel.Close()  
    ```  

    > [!IMPORTANT]
    >  You must close the channel after you have finished processing the POLLINGSTMT operation. Failure to close the channel may affect the behavior of your code.  

12. Close the listener when you are finished receiving data-changed messages.  

    ```  
    listener.Close()  
    ```  

    > [!IMPORTANT]
    >  Closing the listener does not close channels created using the listener. You must explicitly close each channel created using the listener.  

### Example  
 The following example shows a polling query that executes the Employee table. The polling statement performs the following tasks:  

- Selects all the records from the Employee table.  

- Executes the MOVE_EMP_DATA stored procedure to move all records from Employee table to EmployeeHistory table.  

- Executes the ADD_EMP_DETAILS stored procedure to add a single record to the Employee table.  

  The polling messages are saved at `C:\PollingOutput.xml`.  

```  
using System;  
using Microsoft.Adapters.Sql;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  

using System.Xml;  

namespace ConsoleApplication1  
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

                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  

                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  

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
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
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
[Develop SQL applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)