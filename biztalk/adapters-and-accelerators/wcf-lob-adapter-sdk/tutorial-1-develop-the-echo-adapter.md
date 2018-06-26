---
title: "Tutorial 1: Develop the Echo Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffb0df3c-cd07-4bcf-af69-971065081fd6
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial 1: Develop the Echo Adapter
In this tutorial, you will develop a functional adapter using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. The adapter simulates the operations of a fictitious line-of-business system to illustrate many of the key features of the WCF LOB Adapter SDK including:  

- Synchronous Inbound  

- Synchronous Outbound  

- Metadata Browse  

- Metadata Search  

- Metadata Resolve  

  This section contains various features supported by the echo adapter. They are message exchange, operation metadata, connection properties, and adapter properties.  

## Message Exchange Patterns  
 The echo adapter supports the following two message exchange patterns:  

- Synchronous outbound, that is, the consuming client sends the WCF request message via the adapter to the target system, and then waits to receive a WCF response message from the target system via the adapter. This is the most common message exchange pattern for an adapter. To support synchronous outbound, implement the  `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` interface.  

- Synchronous inbound, that is, the consuming client listens for data or events from the target system via the adapter. To support synchronous inbound, implement the  `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface.  

  For more information about the message exchange patterns, see [Architecture overview](architecture-overview-of-the-wcf-lob-adapter-sdk.md).  

> [!NOTE]
>  The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] shows the message exchange pattern as data flow in the UI.  

## Metadata Support  
 The echo adapter supports metadata browsing, searching, and resolving capabilities. Typically, the browsing and searching retrieve operations from an LOB system. For the echo adapter, an LOB system is a set of predefined operations, as shown below:  

```  
EchoMainCategory  
        Echo/EchoStrings  
        Echo/EchoGreetings  
        Echo/EchoCustomGreetingFromFile  
        Echo/OnReceiveEcho  
```  

 The following is the definition of each operation:  

|**Name**|**Operation Definition**|**Description**|**Direction**|  
|--------------|------------------------------|---------------------|-------------------|  
|EchoMainCategory|Category|Categorizes the operations.|N/A|  
|Echo/EchoStrings|string[] EchoStrings(string data)|Echoes the incoming string a specified number of times to the calling client.|Outbound|  
|Echo/EchoGreetings|Greeting[] EchoGreetings(Greeting greeting)|Echoes the incoming Greeting object a specified number of times to the calling client.|Outbound|  
|Echo/EchoCustomGreetingFromFile|CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath)|Echoes the Greeting object by reading its instance from a file. The Greeting object's metadata is obtained from a predefined XSD file.|Outbound|  
|Echo/OnReceiveEcho|void OnReceiveEcho(Uri path, long content)|Echoes the location and length of a file dropped in the specified folder.|Inbound|  

## Adapter Properties  
 The adapter exposes the following adapter properties.  


|            **Name**            | **Category** | **Data Type**  |                                                                                                              **Description**                                                                                                               |
|--------------------------------|--------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|             Count              |     Misc     |  System.Int32  |                                                                    Used to echo the input the specified number of times to the calling client.<br /><br /> Default = 5                                                                     |
|    EnableConnectionPooling     |     Misc     | System.Boolean | Used to enable or disable connection pooling for the adapter.<br /><br /> Default = true, meaning that the connection pooling is enabled in runtime engine of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. |
|       InboundFileFilter        |   Inbound    | System.String  |                                                   Used for the inbound scenario only and used by the FileSystemWatcher to monitor the files of the extension.<br /><br /> Default=\*.txt                                                   |
| InboundFileSystemWatcherFolder |   Inbound    | System.String  |                                        Used to set the folder where the files will be dropped for FileSystemWatcher to raise notification to the adapter.<br /><br /> Default = c:\inbound\watcher.                                        |

## Connection Properties  
 The echo adapter exposes the following connection properties.  

|**Name**|**Data Type**|**Description**|  
|--------------|-------------------|---------------------|  
|Application|System.String|The application name within the LOB system. This property is for illustrative purpose. The echo adapter does not involve any LOB system.<br /><br /> Default = lobapplication|  
|EnableAuthentication|System.Boolean|When true, the adapter expects a value in the username field within the client credentials.<br /><br /> Default = false|  
|Hostname|System.String|The server name where an LOB system resides. This property is for illustrative purpose. The echo adapter does not involve any LOB system.<br /><br /> Default = lobhostname|  

## Interface Implementation  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] defines a collection of classes and interfaces that must be implemented to support specific features of the adapter. The following table describes those classes and interfaces, their descriptions, and when to implement them.  


|                       **Class/Interface**                       |                                                                                       **When to implement**                                                                                        |                                                                                      **Description**                                                                                       |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       Microsoft.ServiceModel.Channels.Common.IConnection        |                                                                     If you need to define the connection to the target system.                                                                     |                                                                        Defines the connection to the target system.                                                                        |
|    Microsoft.ServiceModel.Channels.Common.IConnectionFactory    |                                                                      If you need to create a connection to the target system.                                                                      |                                                                        Creates the connection to the target system.                                                                        |
|      Microsoft.ServiceModel.Channels.Common.ConnectionUri       | If you need to manage a connection Uri.<br /><br /> If you need to categorize connection property within the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool. |                                                                      Manages a connection Uri for the target system.                                                                       |
| Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler |                                                                       Your adapter must support metadata resolve capability.                                                                       |                                                                           Resolves operation and type metadata.                                                                            |
|  Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler  |                                                                        If your adapter supports metadata search capability.                                                                        |                                                                   Searches for the operations within the target system.                                                                    |
|  Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler  |                                                                            Your adapter must support browse capability                                                                             |                                                                    Browses for the operations within the target system.                                                                    |
|     Microsoft.ServiceModel.Channels.Common.IOutboundHandler     |                                                                  If your adapter typically needs to support outbound capability.                                                                   | Transforms the incoming WCF request message into a target system message, invokes target system specific function, and then transforms the response into an outgoing WCF response message. |
|     Microsoft.ServiceModel.Channels.Common.IInboundHandler      |                                                                            If your adapter supports inbound capability.                                                                            |                                                                   Listens for data and/or events from the target system.                                                                   |

 To simplify your adapter development, use the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] to generate your adapter project, which creates a set of derived classes tailored to your adapter features.  

 To customize the adapter and connection properties through the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] tools, modify the following files generated by [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)].  

- {Projectname}BindingElement.cs  

- {Projectname}BindingElementExtensionElement.cs  

- {Projectname}ConnectionUri.cs  

  For details on how to do so, see [Step 2: Categorize the Adapter and Connection Properties](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md).  

## See Also  
 [Tutorials to learn the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)