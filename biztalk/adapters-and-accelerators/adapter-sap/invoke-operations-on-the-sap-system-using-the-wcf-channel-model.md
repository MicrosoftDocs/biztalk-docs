---
title: "Invoke Operations on the SAP System Using the WCF Channel Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF channel model, supporting BAPI transactions"
  - "WCF channel model, invoking operations on the SAP system"
ms.assetid: 80ed85ff-360d-4b7f-a119-cd2a99c21cf4
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invoke Operations on the SAP System Using the WCF Channel Model
You invoke operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using an **IRequestChannel** or **IOutputChannel** channel shape to send messages to the adapter. The basic pattern is to create a channel factory for the required channel shape by using a binding (**SAPBinding**) and an endpoint created from a connection URI. You then create a **Message** instance that represents a SOAP message that conforms to the message schema for your target operation. You can then send this **Message** to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by using a channel created from the channel factory. If you are using an **IRequestChannel**, you receive a response. If there is a problem executing the operation on the SAP system, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] throws a **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.  
  
 For an overview of how to send operations using an **IRequestChannel** in WCF, see [Client Channel-Level Programming](https://msdn.microsoft.com/library/ms788970.aspx).  
  
 The sections in this topic provide information to help you invoke operations on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] using the WCF channel model.  
  
## Supporting BAPI Transactions in the WCF Channel Model  
 All BAPIs that are invoked using the same SAP connection are part of the same Logical Unit of Work (LUW) -- or transaction -- on the SAP system. Each WCF channel represents a unique connection to the SAP system. To support BAPI transactions using the WCF channel model:  
  
- Ensure that every BAPI in an LUW (transaction) is sent over the same channel. This includes the BAPI_TRANSACTION COMMIT or the BAPI_TRANSACTION_ROLLBACK operations.  
  
- Ensure that you close any response message received for a BAPI before you invoke the next BAPI on the channel. (You should do this for every operation; but it is especially important for BAPIs.)  
  
  For more information about BAPI transactions, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).  
  
## Streaming Flat File IDOCs to the SAP Adapter  
 You use the SendIdoc operation to send a flat file (string) IDOC to the adapter. The IDOC data is represented as a string under a single node in this operation. For this reason, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports node-value streaming on the request message. To perform node-value streaming, you must create the request message for the SendIdoc operation by using a **System.ServiceModel.Channels.BodyWriter** that is capable of streaming the IDOC data. For information about how to do this, see [Streaming Flat-File IDOCs in SAP using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).  
  
## How Do I Invoke an Operation by Using a Channel?  
 To invoke an operation by using an **IRequestChannel**, perform the following steps.  
  
#### How to invoke an operation by using an instance of IRequestChannel  
  
1. Build a channel factory (**ChannelFactory\<IRequestChannel\>**). To do this, you must specify a binding (**SAPBinding**) and an endpoint address. You can specify the binding and endpoint address either imperatively in your code or declaratively in configuration. You should set any binding properties required for the operations that you will send before you open the factory. For more information about how to specify the binding and endpoint address in configuration, see [Create a channel using SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md).  
  
   ```  
   // Create a binding  
   SAPBinding binding = new SAPBinding();  
   // Create an endpoint address by using the connection URI  
   EndpointAddress endpointAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
   // Create the channel factory  
   ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
   ```  
  
2. Set the user name password credentials for the channel factory by using the **ClientCredentials** property.  
  
   ```  
   factory.Credentials.UserName.UserName = "YourUserName";  
   factory.Credentials.UserName.Password = "YourPassword";  
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
  
5. Create a **Message** instance for the target operation. Be sure that the message action for the target operation is specified. In this example, the message body is passed by creating an **XmlReader** over a string. The target operation invokes the SD_RFC_CUSTOMER_GET RFC on an SAP system.  
  
   ```  
   string inputXml = "\<SD_RFC_CUSTOMER_GET xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
   //create an XML reader from the input XML  
   XmlReader reader = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
   //create a WCF message from our XML reader  
   Message inputMessge = Message.CreateMessage(MessageVersion.Soap11, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", reader);  
   ```  
  
6. Invoke the **Request** method on the channel to send the message to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and receive the reply. If the SAP system encounters an exception, the adapter throws a **TargetSystemException**. (Other exceptions are possible for non SAP exceptions.) You can get a description of the SAP error from the **InnerException.Message** property of the **TargetSystemException**.  
  
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
  
10. 
  
    You follow the same steps to send a message using the **IOutputChannel** shape except:  
  
-   You create a **ChannelFactory\<IOutputChannel\>** in step 1.  
  
-   You call the **Send** method on the channel in step 6. `channel.Send(messageIn);`.  
  
-   There is no response message returned for an **IOutputChannel**.  
  
### Example  
 The following example shows how to invoke an RFC by using an **IRequestChannel** channel. This example invokes the SD_RFC_CUSTOMER_GET RFC to get a list of customers whose names start with "AB". The response message is consumed by using an **XmlReader** and the customer number and name of each customer returned is written to the console.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.Xml;  
using System.IO;  
  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel.Channels;  
  
namespace SapRfcClientCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //create a binding  
            SAPBinding binding = new SAPBinding();  
  
            //set up an endpoint address.  
            EndpointAddress endpointAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
            //create a channel factory, capable of sending a request to SAP and receiving a reply (IRequestChannel)  
            ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress);  
  
            // add credentials  
            factory.Credentials.UserName.UserName = "YourUserName";  
            factory.Credentials.UserName.Password = "YourPassword";  
  
            //open the factory  
            factory.Open();  
  
            //obtain a channel from the factory by specifying the address you want to connect to  
            IRequestChannel channel = factory.CreateChannel();  
  
            //open the channel  
            channel.Open();  
  
            //create an XML message to send to the SAP system  
            //We are invoking the SD_RFC_CUSTOMER_GET RFC.  
            //The XML below specifies that we want to search for customers with names starting with "AB"  
            string inputXml = "<SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
            //create an XML reader from the input XML  
            XmlReader readerOut = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
            //create a WCF message from the XML reader  
            Message messageOut = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", readerOut);  
  
            //send the message to SAP and obtain a reply  
            Message messageIn = channel.Request(messageOut);  
  
            // Write the KUNNR and NAME1 fields for each returned record to the Console  
            Console.WriteLine("Results of SD_RFC_CUSTOMER_GET");  
            Console.WriteLine("KUNNR\t\tNAME1");  
  
            XmlReader readerIn = messageIn.GetReaderAtBodyContents();  
  
            while (readerIn.Read())  
            {  
                if (readerIn.IsStartElement())  
                {  
                    switch (readerIn.Name)  
                    {  
                        case "RFCCUST":  
                            Console.Write("\n");  
                            break;  
  
                        case "KUNNR":  
                            readerIn.Read();  
                            Console.Write(readerIn.ReadString() + "\t");  
                            break;  
  
                        case "NAME1":  
                            readerIn.Read();  
                            Console.Write(readerIn.ReadString() + "\t");  
                            break;  
  
                        default:  
                            break;  
                    }  
                }  
            }  
  
            // return the cursor  
            Console.WriteLine();  
  
            // Close the input reader  
            readerIn.Close();  
  
            // Close the input message. You should do this for every message you   
            // send on the channel  
            messageIn.Close();  
  
            // close the channel when you are done using it.  
            channel.Close();  
  
            //close the factory  
            //note: closing the factory will close all of its channels.  
            factory.Close();  
        }  
    }  
}  
```  
  
## See Also  
[Develop applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)