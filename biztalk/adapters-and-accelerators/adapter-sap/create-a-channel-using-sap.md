---
title: "Create a channel using SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "channel programming, creating a channel"
  - "how to, create a channel"
  - "creating a channel"
  - "WCF channel model, creating a channel"
ms.assetid: 24af1465-bb60-41d7-98bd-e501a981f82a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create a channel using SAP
In the WCF channel model, you invoke operations on the SAP system or receive messages from the SAP system by exchanging SOAP messages with the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] over a WCF channel.  
  
- You invoke operations (outbound operations) by using either an **IRequestChannel** or an **IOutputChannel** to send messages to the adapter  
  
- You receive messages (triggered from the SAP system) over an **IReplyChannel**.  
  
  The topics in this section provide information about how to create and configure channel shapes that are used for inbound and outbound operations.  
  
## Creating Outbound (Client) Channels  
 You can use either an **IRequestChannel** or an **IOutputChannel** to invoke operations on the SAP system. In either case, you first create a **System.ServiceModel.ChannelFactory** using the appropriate interface. You then use the factory to create the channel. After you have created the channel you can use it to invoke operations on the adapter.  
  
#### To create and open an outbound channel  
  
1. Create and initialize an instance of **ChannelFactory** for the desired channel shape by using an endpoint and a binding. The endpoint specifies an SAP connection URI and the binding is an instance of **SAPDBBinding**. (Set any binding properties required before you open the channel factory.)  
  
2. Provide SAP credentials for the channel factory by using the **ClientCredentials** property.  
  
3. Open the channel factory.  
  
4. Get an instance of the channel by invoking the **CreateChannel** method on the channel factory.  
  
5. Open the channel.  
  
   You can specify the binding and endpoint address in your code or from configuration.  
  
### Specifying the Binding and Endpoint Address in Code  
 The following code example shows how to create an **IRequestChannel** by specifying the binding and endpoint address in code. The code to create an **IOutputChannel** is the same except that you must specify an **IOutputChannel** interface for the **ChannelFactory** and channel type.  
  
```  
// Create binding -- set binding properties before you open the factory.  
SAPBinding sapBinding = new SAPBinding();  
  
// Create address.  
EndpointAddress sapAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
// Create channel factory from binding and address.  
ChannelFactory<IRequestChannel> factory =   
    new ChannelFactory<IRequestChannel>(sapBinding, sapAddress);  
  
// Specify credentials.   
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
  
// Open the factory  
factory.Open();  
  
// Get channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
### Specifying the Binding and Endpoint Address in Configuration  
 The following code example shows how to create a channel factory from a client endpoint specified in configuration.  
  
```  
// Create channel factory from configuration.  
ChannelFactory<IRequestChannel> factory =  
new ChannelFactory<IRequestChannel>("MyRequestChannel");  
  
// Specify credentials.  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
  
// Open the factory.  
factory.Open();  
  
// Get a channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
#### The Configuration Settings  
 The following code shows the configuration settings used for the preceding example. The contract for the client endpoint must be "System.ServiceModel.Channels.IRequestChannel" or "System.ServiceModel.Channels.IRequestChannel" depending on the kind of channel shape that you want to create.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <sapBinding>  
                <binding name="SAPBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" enableBizTalkCompatibilityMode="false"  
                    receiveIdocFormat="Typed" enableSafeTyping="false" generateFlatFileCompatibleIdocSchema="true"  
                    maxConnectionsPerSystem="50" enableConnectionPooling="true"  
                    idleConnectionTimeout="00:15:00" flatFileSegmentIndicator="SegmentDefinition"  
                    enablePerformanceCounters="false" autoConfirmSentIdocs="false"  
                    acceptCredentialsInUri="false"  
                    padReceivedIdocWithSpaces="false" sncLibrary="" sncPartnerName="" />  
            </sapBinding>  
        </bindings>  
        <client>  
            <endpoint address="sap://CLIENT=800;LANG=EN;@a/ADAPSAP47/00?RfcSdkTrace=False&AbapDebug=False"  
                binding="sapBinding" bindingConfiguration="SAPBinding" contract="System.ServiceModel.Channels.IRequestChannel"  
                name="MyRequestChannel" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### Creating Inbound (Service) Channels  
 You configure the adapter to receive inbound messages from an SAP system by setting binding properties on an instance of **SAPBinding**. You then use this binding to build a channel listener from which you can get an **IReplyChannel** channel to receive operations from the adapter.  
  
##### To create and open an IReplyChannel to Receive Data-changed Notifications  
  
1. Create an instance of **SAPBinding**.  
  
2. Set any binding properties required for the operations you want to receive. Be sure to set the **AcceptCredentialsInUri** binding property.  
  
3. Create a **BindingParameterCollection** and add an **InboundActionCollection** that contains the actions of the operations that you want to receive. The adapter will return an exception to the SAP system for all other operations. This step is optional. For more information, see [Receiving Inbound Operations from the SAP System by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).  
  
4. Create a channel listener by invoking **BuildChannelListener\<IReplyChannel\>** method on the **SAPBinding**. You specify the SAP connection URI as one of the parameters to this method. The connection URI must contain parameters for an RFC Destination on the SAP system. For more information about the SAP connection URI, see The [Create the SAP System Connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md). If you created a **BindingParameterCollection** in step 3, you also specify this when you create the channel listener.  
  
5. Open the listener.  
  
6. Get an **IReplyChannel** channel by invoking the **AcceptChannel** method on listener.  
  
7. Open the channel.  
  
   The following code shows how to create a channel listener and get an **IReplyChannel** to receive operations from the adapter.  
  
```  
// Create a binding and specify any binding properties required  
// for the opreations you want to receive  
SAPBinding binding = new SAPBinding();  
  
// Set AcceptCredentialsInUri because the URI must contain credentials.  
binding.AcceptCredentialsInUri = true;  
  
// Create an InboundActionCollection and add the message actions to listen for,  
// only the actions added to the InboundActionCollection are received on the channel.  
// In this case a single action is specified: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD  
InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD");  
  
// Create a BindingParameterCollection and add the InboundActionCollection  
BindingParameterCollection bpcol = new BindingParameterCollection();  
bpcol.Add(actions);  
  
// Create the channel listener by specifying  
// the binding parameter collection (to filter for the Z_RFC_MKD_ADD action) and   
// a connection URI that contains listener parameters.  
Uri listeneraddress =  
new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
listener = binding.BuildChannelListener<IReplyChannel>(connectionUri, new BindingParameterCollection());  
listener.Open();  
  
// Get a channel from the listener and open it.  
channel = listener.AcceptChannel();  
channel.Open();  
```  
  
## See Also  
[Develop applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)