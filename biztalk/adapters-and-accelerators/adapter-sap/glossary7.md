---
title: "Glossary for the mySAP adapter in BizTalk | Microsoft Docs"
description: Common terms and definitions used by the mySAP adapter in the BizTalk Adapter pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87db79be-e242-40fa-9897-8915e6fb5cae
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Glossary
The following terms and definitions are used in [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
## A  
  
**adapter**  
A WCF-based component that helps exchange messages between applications (for example, a line-of-business system) and BizTalk Server. The adapter consists of design-time components and run-time components for receive and send operations.

**adapter client**  
An application that interacts with a line-of-business (LOB) system through the adapter.

**Advanced Business Application Programming (ABAP)**  
The SAP programming language.  
  
## B  
  
**BAPIs (Business Application Programming Interfaces)**  
Standard interfaces exposed by the SAP system to exchange business between SAP and other systems. BAPIs are used to integrate different components, which are connected to each other over a local network or on the Internet.

**binding**  
A process by which software components and layers are linked together. When a network component is installed, the binding relationships and dependencies for the components are established. Binding allows components to communicate with each other. In BizTalk Server, an established mapping between an orchestration adapter-agnostic endpoint (port or role link) and physical adapter-specific endpoints (send/receive ports or party).

**BizTalk Server**  
Connects diverse software. BizTalk Server enables you to create and modify process logic that uses that software. BizTalk Server also enables information workers to monitor running processes, interact with trading partners, and perform other business-oriented tasks.

**business object**  
Encapsulates SAP data and processes in an object-oriented model. External clients invoke methods called business object application interfaces (BAPIs) to act on the object (and its underlying SAP artifacts). By default, the SAP adapter does not expose business objects to consuming applications. Business objects are only available for client operations.

**Business Object Repository (BOR)**  
Contains all of the SAP business object types and SAP interface types, as well as their components (such as methods and attributes), resident on the SAP R/3 system.  
  
## C  
  
**channel**  
A concrete implementation of a binding element. The binding represents the configuration, and the channel is the implementation associated with that configuration. Therefore, there is a channel associated with each binding element. Channels stack on top of each other to create the concrete implementation of the binding: the channel stack.

**code page** 
Essentially a matrix of code points. All data in the database, including characters, is stored as byte sequences. For character data, a code page is the mapping between a byte sequence and a character.

**connection URI**  
A string that identifies a resource in a distributed environment. Adapters use a connection Uniform Resource Identifier (URI) that contains the information necessary to establish a connection with the LOB system.

**contract**  
Specifies the collection and structure of messages required to access the operations offered by the service.
  
####  <a name="D"></a> D  
  
**design-time experience**  
Procedures and operations that a developer performs during design time; for example, using the Consume Adapter Service BizTalk Project Add-in to retrieve message schemas.  
  
## E  
**endpoint address**  
A network address that identifies the location of a Windows Communication Foundation (WCF) service endpoint. For an adapter, the endpoint address is expressed as a connection Uniform Resource Identifier (URI) that contains location and connection parameters. The adapter can use these to establish a connection to the underlying line-of-business (LOB) system.

**Enterprise Single Sign-on system (SSO)**  
An SSO database, a master secret server, and one or more Enterprise Single Sign-On (SSO) servers. These servers do the mapping between the Windows and non-Windows credentials, look up the credentials in the SSO database, and are used for administering the SSO system. The SSO database is also used as a configuration store to hold custom configuration data for adapters.

**Extensible Markup Language (XML)**  
A markup language designed to describe data. XML tags are not predefined.  
  
## F  
  
**function modules**  
Procedures defined in an SAP system as ABAP programs. These are part of function groups that contain a logical grouping of function modules. Function modules enable SAP clients to reuse and encapsulate global functions.
  
## G  
  
**global assembly cache (GAC)**  
A machine-wide code cache that stores assemblies specifically installed to be shared by many applications on the computer. Applications deployed in the global assembly cache must have a strong name.
  
## I  
  
**inbound operation**  
An operation that is invoked by a line-of-business (LOB) system on the adapter.
  
**intermediate document (IDOC)**  
A structured document that is used to exchange data between R/3, R/2 and non-SAP systems.  
  
## M  
  
**metadata**  
In WCF, refers to a description of the contract exposed by a service. This is known as the service description and is expressed in a WSDL document. The metadata exposed by an adapter describes the (interface to) the operations that it can perform on the underlying line-of-business (LOB) system.

**[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]**  
The specifications for building BizTalk adapters using open standards based on Web services.  
  
## O  
  
**one-way**  
A message exchange pattern (MEP) in which the sender sends a message, but no response is returned by the receiver. In BizTalk Server, MEPs are referred to as communication patterns.

**outbound operation**  
An operation that is invoked by the adapter on the line-of-business system (LOB).
  
**output.cs**  
The default output file created by the ServiceModel Metadata Utility tool (svcutil.exe).  
  
## P  
  
**polling**  
A technique that device drivers use to find out from multiple devices whether they contain data to transmit. The devices are polled one at a time.

**program ID**  
Unique channel to send an RFC in the configured gateway. The program ID or host name and the SAP gateway service, provided for the program ID, must match the registration parameters (via RfcAccept).

**proxy**  
In WCF, refers to a managed-code object that implements the service contract exposed by a service. The WCF service model is based on the use of such proxies. In the WCF service model, the service contract is expressed as a .NET interface.
  
## R  
  
**Remote Function Call (RFC)**  
A procedure for data exchange between a client and server. Typically the client calls a server program, and the server returns the results via a TCP/IP connection.
  
**request-response**  
A message exchange pattern (MEP) in which the sender sends a request message and expects a response message from the receiver. In BizTalk Server, MEPs are referred to as communication patterns. Depending on the messaging technology and the direction of the request message (inbound or outbound), this pattern is also called request-reply or solicit-response.

**run-time experience**  
Procedures and operations performed by a developer during run time or when deploying a solution; For example, creating a physical port binding from the BizTalk Server Administration console.
  
## S  
  
**schema**  
The structure for a message. A schema can contain multiple subschema.
  
**ServiceModel Metadata Utility Tool (svcutil.exe)**  
A command-line utility that is included with WCF. It is used to create service model proxy code from the service description (metadata) that is exposed by a WCF service such as an adapter. For outbound operations, the tool creates a WCF client class and helper code; for inbound operations, the tool creates a WCF service contract and helper code.

**SOAP (Simple Object Access Protocol)**  
A simple, XML-based protocol for exchanging structured and type information in decentralized, distributed environments. WCF is based on the exchange of SOAP messages between clients and services to invoke operations and return results.

**SOAP message**  
A well-formed XML document. It should use the SOAP envelope and SOAP encoding namespaces and include an optional XML declaration, followed by a SOAP envelope (the root element), which is made up of an optional SOAP header and a SOAP message body.

**SQL Server Integration Services (SSIS)**  
A component that is used to import, export, and transform data from different data sources. Previously called data transformation service (DTS).
  
**strongly-typed data**  
A data set or result set that is bound to an underlying object type. Each row in a strongly-typed XML data set is composed of typed, named elements that correspond to fields of the underlying object type.

  
## T  
  
**transaction ID (TID)**  
A globally-unique identifier that SAP associates with each logical unit of work (LUW).  
  
 
## W  
  
**WCF channel model**  
A programming model that relies on several interfaces and other types. Channels provide a low-level programming model for sending and receiving messages.
  
**WCF client**  
A client-application construct that exposes the service operations as methods. You can use the Add Adapter Service Reference Visual Studio Plug-in or the ServiceModel Metadata Utility Tool to generate a WCF client class from the metadata exposed by an adapter.

**WCF service contract**  
A managed-code representation of the service contract. It is expressed as an interface in which classes and methods are attributed to define the service, operation, message, and data contracts used to communicate with a service. You can use the ServiceModel Metadata Utility tool or the Add Adapter Service Reference Visual Studio Plug-in to generate a WCF service contract from the metadata exposed by an adapter. You implement the WCF service contract to receive operations from an LOB system.

**WCF service model**  
A WCF programming model in which a service is represented as a managed code object. The operations exposed by the service are represented as methods with strongly-typed data.

**weakly-typed data**  
A data set or result set that is not bound to an underlying object type. Each row in a weakly-typed XML data set is composed of a collection of generic columns in which attributes describe the name and type of each element.

**Web services**  
A unit of application logic providing data and services to other applications. Applications access XML Web services using standard Web protocols and data formats such as HTTP, XML, and SOAP, independent of how each XML Web service is implemented. XML Web services combine the best aspects of component-based development and the Web, and are a cornerstone of the Microsoft .NET programming model.

**Web Services Description Language (WSDL)**  
An XML-based language that describes a service as a set of endpoints that operate on messages. The WSDL document describes the service contract, operation contracts, message contracts, and data contracts that a client must use to interface with the service.

**Windows Communication Framework (WCF)**  
A Microsoft service-oriented communication infrastructure. The framework inherently provides clients with a service programming model and a channel programming model for finer control of message exchanges.

**WS-Metadata Exchange (MEX) endpoint**  
An endpoint exposed by a WCF service, such as an adapter, that implements the **IMetadataExchange** interface. A WS-Metadata Exchange endpoint can be used to retrieve a service description (WSDL) for operations exposed by an adapter on the target system.  
  
## X  
  
**XML Schema definition language (XSD)**  
A schema language. An XML Schema defines the elements, attributes, and data types that comply with the World Wide Web Consortium (W3C) XML Schema Part 1: Structures Recommendation for the XML Schema Definition Language. The W3C XML Schema Part 2: Datatypes Recommendation is the recommendation for defining data types that are used in XML schemas. The XML Schema definition language enables you to define the structure and data types for XML messages.