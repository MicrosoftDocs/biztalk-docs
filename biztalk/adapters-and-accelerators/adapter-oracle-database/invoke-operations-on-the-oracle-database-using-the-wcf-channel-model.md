---
title: "Invoke Operations on the Oracle Database Using the WCF Channel Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "invoking operations, using the WCF channel model"
  - "WCF channel model, invoking operations"
  - "invoking operations"
  - "operations, invoking"
ms.assetid: 6dd95c18-8f78-46d0-8845-b74890614c33
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invoke Operations on the Oracle Database Using the WCF Channel Model
You can invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using an **IRequestChannel** or **IOutputChannel** shape to send messages to the adapter. The basic pattern is to create a channel factory for the required channel shape by using a binding (**OracleDBBinding**) and an endpoint created from a connection URI. You then create a **Message** instance that represents a SOAP message that conforms to the message schema for your target operation. You can then send this **Message** to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using a channel created from the channel factory. If you are using an **IRequestChannel**, you receive a response. If there is a problem executing the operation on the Oracle database, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] throws a **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.  
  
 For an overview of how to send operations using an **IRequestChannel** in WCF, see "Client Channel-Level Programming" at [http://go.microsoft.com/fwlink/?LinkId=106081](http://go.microsoft.com/fwlink/?LinkId=106081).  
  
 The sections in this topic provide information to help you invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] using the WCF channel model.  
  
## Creating and Consuming Messages for Outbound Operations  
 To invoke an operation on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you send the request message for the target operation using either an **IRequestChannel** or an **IOutputChannel**. If you use an **IRequestChannel** the adapter returns the results of the operation in the response message.  
  
 For more detailed information about the request and response message schemas and the message actions for each operation, see [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).  
  
 How you create the request message and consume the response message determines whether node streaming or node-value streaming is performed by the adapter. This in turn determines whether end-to-end streaming of LOB data is performed for supported operations.  
  
### Creating the request message  
 You can create the request message in one of two ways:  
  
- To create a message that can be used for node-value streaming you must pass the message body in an **XmlBodyWriter** that implements node-value streaming.  
  
- To create a message that can be used for node streaming you can pass the message body in an **XmlReader**.  
  
  You typically use node-value streaming to support end-to-end streaming of Oracle LOB data in the request message. The only operation that supports this feature is UpdateLOB.  
  
### Consuming the response message  
 You can consume the response message in one of two ways:  
  
- To consume the message using node-value streaming you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.  
  
- To consume the message using node streaming you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.  
  
  You typically use node-value streaming to support end-to-end streaming of Oracle LOB data in the response message. There are many operations that support this feature.  
  
### LOB Data and Message Streaming Support  
 For more information about how the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports streaming on LOB data, see [Streaming large object data types in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).  
  
 For more information about implementing node-value streaming in your code to support end-to-end streaming of LOB data, see [Streaming Oracle Database LOB Data Types Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).  
  
## Transaction Support on Outbound Operations in the WCF Channel Model.  
 The adapter executes each operation you invoke inside a dedicated transaction on the Oracle database. You can control the isolation level of these transactions by setting the **TransactionIsolationLevel** binding property.  
  
## About the Examples Used in this Topic  
 The example in this topic uses the SCOTT.ACCOUNTACTIVITY table. A script to generate these artifacts is supplied with the SDK samples. For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).  
  
## How Do I Invoke an Operation by Using a Channel?  
 To invoke an operation by using an **IRequestChannel**, perform the following steps.  
  
#### How to invoke an operation by using an instance of IRequestChannel  
  
1. Build a channel factory (**ChannelFactory\<IRequestChannel\>**). To do this, you must specify a binding (**OracleDBBinding**) and an endpoint address. You can specify the binding and endpoint address either imperatively in your code or declaratively in configuration. For more information about how to specify the binding and endpoint address in configuration, see [Create a channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md).  
  
   ```  
   // Create a binding  
   OracleDBBinding binding = new OracleDBBinding();  
   // Create an endpoint address by using the connection URI  
   EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
   // Create the channel factory  
   ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
   ```  
  
2. Set the user name password credentials for the channel factory by using the **ClientCredentials** property.  
  
   ```  
   factory.Credentials.UserName.UserName = "SCOTT";  
   factory.Credentials.UserName.Password = "TIGER";  
   ```  
  
3. Open the channel factory.  
  
   ```  
   factory.Open();  
   ```  
  
4. Get a channel from the factory and open it.  
  
   ```  
   IRequestChannel channel = factory.CreateChannel();  
   channel.Open();  
   ```  
  
5. Create a **Message** instance for the target operation. Be sure that the message action for the target operation is specified. In this example, the message body is passed by creating an **XmlReader** over a file. The target operation is a Select operation on the SCOTT/EMP table.  
  
   ```  
   XmlReader readerIn = XmlReader.Create("SelectAllActivity.xml");  
   Message messageIn = Message.CreateMessage(MessageVersion.Default,  
       "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select",  
       readerIn);  
   ```  
  
6. Invoke the **Request** method on the channel to send the message to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] and receive the reply. If the Oracle database encounters an exception, the adapter throws a **TargetSystemException**. (Other exceptions are possible for non Oracle exceptions.) You can get a description of the Oracle error from the **InnerException.Message** property of the **TargetSystemException**.  
  
   ```  
   try  
   {  
       Message messageOut = channel.Request(messageIn);  
   }  
   catch (Exception ex)  
   {  
       // handle exception  
   }  
   ```  
  
7. Process the response. In this example, **GetReaderAtBodyContents** is called on the response message to get the message body.  
  
   ```  
   XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
   ```  
  
8. When you are done processing the response message, close the reader and the message.  
  
   ```  
   readerOut.Close();  
   messageOut.Close();  
   ```  
  
9. When you are done using the channel and the channel factory, close them. Closing the factory will close all channels that were created with it.  
  
    ```  
    channel.Close()  
    factory.Close();  
  
    ```  
  
   You follow the same steps to send a message using the **IOutputChannel** shape except:  
  
-   You create a **ChannelFactory\<IOutputChannel\>** in step 1.  
  
-   You call the **Send** method on the channel in step 6. `channel.Send(messageIn);`.  
  
-   There is no response message returned for an **IOutputChannel**.  
  
### Example  
 The following example shows how to invoke a Select operation by using an **IRequestChannel** channel. The Select response message is consumed by using an **XmlReader** and the number of records returned is written to the console.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
using System.Xml;  
using System.IO;  
using System.Runtime.Serialization;  
  
namespace RequestChanneSample  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The Select operation request message  
            const string selectRequestString =  
                "\<Select xmlns=\"http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY\"\>" +  
                    "<COLUMN_NAMES>*</COLUMN_NAMES>" +  
                    "<FILTER>ACCOUNT = 100002</FILTER>" +  
                "</Select>";  
            try  
            {  
                // Create binding -- specify binding properties before you open the factory.  
                OracleDBBinding odbBinding = new OracleDBBinding();  
  
                // Create address.  
                EndpointAddress odbAddress = new EndpointAddress("oracledb://ADAPTER/");  
  
                // Create channel factory from binding and address.  
                ChannelFactory<IRequestChannel> factory =   
                    new ChannelFactory<IRequestChannel>(odbBinding, odbAddress);  
  
                // Specify credentials   
                factory.Credentials.UserName.UserName = "SCOTT";  
                factory.Credentials.UserName.Password = "TIGER";  
  
                // Open the factory.  
                factory.Open();  
  
                // Get a channel.  
                IRequestChannel channel = factory.CreateChannel();  
  
                // Open the channel.  
                channel.Open();  
  
                // Create the request message from the string  
                StringReader strReader = new StringReader(selectRequestString);  
                XmlReader readerIn = XmlReader.Create(strReader);  
  
                Message requestMessage = Message.CreateMessage(MessageVersion.Default,  
                    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select",  
                    readerIn);  
  
                Send the message and get a respone  
                Message responseMessage = channel.Request(requestMessage);  
  
                // Get an XmlReader from the message  
                XmlReader readerOut = (XmlReader) responseMessage.GetReaderAtBodyContents();  
  
                // Count the number of records returned and write to the console.  
                readerOut.MoveToContent();  
                int numberOfRecordsReturned = 0;  
                while (readerOut.Read())  
                {  
                    if (readerOut.NodeType == XmlNodeType.Element && readerOut.Name == "ACCOUNTACTIVITYRECORDSELECT")  
                        numberOfRecordsReturned++;  
                }  
  
                Console.WriteLine("{0} records returned.", numberOfRecordsReturned);  
  
                // Close the output reader and message  
                readerOut.Close();  
                responseMessage.Close();  
  
                //Close channel  
                channel.Close();  
  
                //Close the factory  
                factory.Close();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
            }  
        }  
    }  
}  
```  
  
## See Also  
 [Develop Oracle Database applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)