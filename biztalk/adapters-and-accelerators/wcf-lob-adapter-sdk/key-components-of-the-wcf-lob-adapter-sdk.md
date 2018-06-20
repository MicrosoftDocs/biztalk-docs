---
title: "Key Components of the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59b8029b-4799-471b-8825-15d79a30bf1f
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Key Components of the WCF LOB Adapter SDK
Developing an adapter using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] requires the use of many of the following basic components:  

- **Connection components** to help establish and maintain a connection to the line-of-business system.  

- **Handler components** define and implement procedures used to work with inbound and outbound messages and metadata operations.  

- **Metadata components** define and manipulate the metadata used to communicate with the line-of-business system.  

- **Custom components** provide support for transactions, reliable messaging, and security.  

- **Core components** tie all of the components together and ensure seamless integration into [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].  

  These components are the focus of this topic.  

## Connection components  
 The connection components include interfaces and classes that help define and control the lifetime of connections as well as manage uniform resource identifiers (URI) query attributes and user attributes. Connection components include the interfaces and classes described in the following table.  

|Connection Component|Required?|Description|  
|---|---|---|  
|`Microsoft.ServiceModel.Channels.Common.ConnectionUri`|Required|Base class for providing a customized URI building experience for users who will consume your adapter.|  
|`Microsoft.ServiceModel.Channels.Common.IConnection`|Required|Interface that defines the behavior for a connection. Developers must implement this interface to define a connection to the target system.|  
|`Microsoft.ServiceModel.Channels.Common.IConnectionFactory`|Required|Base class for a connection factory. Developers will subclass when defining the connection factory for the target system.|  
|`Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`|Optional|Contains settings that control the behavior of the connection pool. Developers may want to tune these values based on the behavior of the target system.|  
|`Microsoft.ServiceModel.Channels.Common.ConnectionManagerSettings`|Optional|Contains static settings that control the behavior of the connection pool. Developers may want to tune these values for their target system.|  

 The [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)] will create implementations of `Microsoft.ServiceModel.Channels.Common.IConnection``Microsoft.ServiceModel.Channels.Common.ConnectionUri` and `Microsoft.ServiceModel.Channels.Common.IConnectionFactory` regardless of the wizard options chosen. These implementations will contain code for supporting options chosen in the wizard (including connection properties in the connection URI) but the adapter developer will have to provide implementations for Open, Close and other methods of `Microsoft.ServiceModel.Channels.Common.IConnection` and `Microsoft.ServiceModel.Channels.Common.ConnectionUri`.  

## Handler components  
 The handler components provide support for different message exchange patterns including inbound, outbound, asynchronous inbound, asynchronous outbound, and metadata search, browse, and resolve operations. Handler components include the interfaces and classes described in the following table.  

|Handler Component|Required?|Description|  
|---|---|---|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncInboundHandler`|Optional|Used to receive messages asynchronously from the target system. Asynchronous support is optional.|  
|`Microsoft.ServiceModel.Channels.Common.IAsyncOutboundHandler`|Optional|Used to send messages asynchronously from the target system. Asynchronous support is optional.|  
|`Microsoft.ServiceModel.Channels.Common.IInboundHandler`|Optional|Used to receive messages from the target system. Developers should implement this handler if the adapter needs to listen for messages from the target system.|  
|`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`|Optional|Provides support for sending messages to the target system. While optional, it is required for the request-response message pattern. Most fundamental communication technologies are based on this pattern including HTTP, RPC, and many others.|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataBrowseHandler`|Optional|This handler is implemented when the adapter supports metadata browse. Though optional, developers will often implement this handler to provide a list of operations available in the target system.|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler`|Optional|This handler must be implemented when the adapter retrieves and returns metadata from the target system that represents system-specific logic and data types. Metadata can be retrieved from the actual target system, or it can be created to represent the capabilities of the target system. For example, an FTP adapter could create GET and PUT operations.<br /><br /> While not required, developers will generally implement this handler to provide information about a specific operation.|  
|`Microsoft.ServiceModel.Channels.Common.IMetadataSearchHandler`|Optional|This handler is implemented when the adapter supports metadata search.|  

 The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] will create implementations of `Microsoft.ServiceModel.Channels.Common.IAsyncOutboundHandler`, `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`, `Microsoft.ServiceModel.Channels.Common.IInboundHandler` and the metadata handlers based on the choices made by the developer. Support code is provided; however, the adapter developer will have to supply code to start and stop the inbound listener and other code marked by TODO comments.  

## Metadata components  
The metadata components provide support for handling metadata requests, and for describing types and operations in the target application. The handler components control how metadata requests are dealt with. The metadata components describe the data types and operations exposed by the target system.  

 The metadata components are designed to hold two types of metadata information: type metadata and operation metadata.  

- *Type metadata* describes the data types that are available in the target system and includes the name of the type, its array properties if it is an array, and whether it is a simple XSD schema type or a complex type.  

- *Operation metadata* describes the operations that are available in the target system. Properties include a return type, a list of parameters, and operation name.  

  Metadata support within an adapter is optional, but recommended. One of the benefits of using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] to build an adapter versus implementing functionality as a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service is the ability to expose and bind to a dynamic set of operations.  

> [!NOTE]
>  If you need to expose a limited set of static methods, you should consider using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].  

  The components available for handling, describing, and working with metadata are described in the following table.  

|Metadata Component|Description|  
|---|---|  
|`Microsoft.ServiceModel.Channels.Common.ComplexQualifiedType`|A class representing a complex qualified type for an adapter. For example, if the target system is a relational database, a table, row, or user-defined procedure return type might all be custom qualified types.|  
|`Microsoft.ServiceModel.Channels.Common.OperationMetadata`|Base class for representing operation metadata for the target system. For example, you could subclass OperationMetadata to contain information about stored procedures in an adapter targeting a relational database.|  
|`Microsoft.ServiceModel.Channels.Common.OperationMetadataTraceRecord`|Provides a way to capture operation metadata to a trace file. The trace collects information such as unique ID, last time accessed, timestamp, display name, original name, parameters, and other details.|  
|`Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata`|Provides a way of defining attributes of an operation such as parameters and return type.|  
|`Microsoft.ServiceModel.Channels.Common.OperationParameter`|Describes a parameter used to invoke an operation on the target system. Properties include the name, original name, parameter direction, and a flag indicating whether the parameter is empty or not.|  
|`Microsoft.ServiceModel.Channels.Common.OperationParameterDirection`|An enumerated type that describes the direction of a parameter for an operation. A parameter can be inbound only (In), outbound only (Out), or bidirectional (InOut).|  
|`Microsoft.ServiceModel.Channels.Common.OperationResult`|Represents an operation result. Can be OperationResult.Empty for operations that return void or null and a string, integer, or other value depending on the operation.|  
|`Microsoft.ServiceModel.Channels.Common.QualifiedType`|Designed to be the base class for qualified type properties and is used to describe properties of type metadata for a target system.|  
|`Microsoft.ServiceModel.Channels.Common.QualifiedTypeContainer`|Provides a container for a set of related qualified types.|  
|`Microsoft.ServiceModel.Channels.Common.SimpleQualifiedType`|Describes the properties of type metadata for a target system when that type maps directly to a W3C XSD schema type. For a list of allowable types, see [XmlTypeCode Enumeration](https://msdn.microsoft.com/library/system.xml.schema.xmltypecode(v=vs.110).aspx).|  
|`Microsoft.ServiceModel.Channels.Common.TypeMember`|Provides a way for defining a simple or complex data member in the structured type metadata.|  
|`Microsoft.ServiceModel.Channels.Common.TypeMetadata`|Base class for representing type metadata for the target system.|  
|`Microsoft.ServiceModel.Channels.Common.StructuredTypeMetadata`|Provides a way of defining a data structure that contains complex and/or simple type members.|  
|`Microsoft.ServiceModel.Channels.Common.TypeMetadataCollection`|Provides a container for a set of related type metadata.|  
|`Microsoft.ServiceModel.Channels.Common.TypeMetadataTraceRecord`|Provides a way to capture type metadata to a trace file. The trace collects information such as unique ID, last time accessed, timestamp, and other details.|  

## Custom Components  
 Custom components provide support for transactions, security, reliable messaging and other features that are highly dependent on the target system. As an adapter developer using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], you will need to understand the capabilities of the target system and determine the extent to which you want to support them.  

## Core Components  
 Core components provide a set of base classes and interfaces that enable the adapter to be plugged into [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]. The core components are described in the following table.  


|                     Core Component                      | Required? |                                                                                                                                                                                          Description                                                                                                                                                                                          |
|---------------------------------------------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `Microsoft.ServiceModel.Channels.Common.Adapter`     | Required  |                                                      The base class of an adapter written using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. It is responsible for interacting with the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel architecture                                                      |
| `Microsoft.ServiceModel.Channels.Common.AdapterBinding` | Required  | Class that contains settings that control various settings for the adapter including the connection pool (`Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`), cache (`Microsoft.ServiceModel.Channels.Common.CacheSettings`), metadata (`Microsoft.ServiceModel.Channels.Common.MetadataSettings`), and messaging (`Microsoft.ServiceModel.Channels.Common.MessagingSettings`). |

 Custom adapters are exposed through WCF bindings. For more information, see the WCF documentation at [http://go.microsoft.com/fwlink/?LinkId=100308](http://go.microsoft.com/fwlink/?LinkId=100308).  

 The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] create implementations of `Microsoft.ServiceModel.Channels.Common.Adapter`, `Microsoft.ServiceModel.Channels.Common.AdapterBinding`, `System.ServiceModel.Configuration.StandardBindingElement`, and `System.ServiceModel.Configuration.StandardBindingCollectionElement` to expose the adapter binding to the WCF configuration system. The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] will also generate an implementation of `System.ServiceModel.Configuration.BindingElementExtensionElement` to enable `Microsoft.ServiceModel.Channels.Common.Adapter` to be used within a WCF custom binding from a computer or application configuration file.  

 For more information about StandardBindingElement, StandardBindingCollectionElement, and BindingElementExtensionElement, see the WCF documentation.  

 For more information about configuring an adapter written with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], see [Deploy an adapter using the WCF LOB adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md).  

## See Also  
 [Understand the LOB system with the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md)