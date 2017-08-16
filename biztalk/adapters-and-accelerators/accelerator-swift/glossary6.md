---
title: "Glossary for SWIFT accelerator in BizTalk Server | Microsoft Docs"
description: Common terms and definitions to know and learn to use the BizTalk Accelerator for SWIFT
ms.custom: ""
ms.date: "08/16/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7331beb-f6a7-4eea-8b31-28f5d15666d0
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Glossary
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for SWIFT uses the following glossary terms and definitions.  
  
## A  
 **assembler**  
 A [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] send pipeline component that is invoked during the assemble stage of outbound pipeline processing. An assembler typically does the job of serializing an outbound message from XML into some flat-file format.  
  
 **assembly**  
 The primary building block of a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)] application. It is the basic unit of reuse, versioning, security, and deployment. It is a collection of files that appear to the programmer to be a single-dynamic link library (DLL) or executable (EXE).  
  
 **assembly cache**  
 A machine-wide code cache used for side-by-side storage of assemblies. There are two parts to the cache. The global assembly cache contains assemblies that are explicitly installed to be shared among many applications on the computer. The download cache stores code downloaded from Internet or intranet sites, isolated to the application that triggered the download so that code downloaded on behalf of one application or page does not affect other applications.  
  
## B  
 **Bank Identifier Code (BIC)**  
 A code used to identify a financial institution, as defined by SWIFT.  
  
 **Business Rule Composer tool**  
 A graphical user interface tool used to compose policies.  
  
 **Business Rule Engine (BRE)**  
 A run-time inference engine that evaluates rules against facts and initiates actions based on the results of that evaluation.  
  
## C  
 **conditional rule**  
 A rule specifying a relationship among fields of a SWIFT message type. Conditional rules are defined in the SWIFT Standards Release Guide.  
  
## D  
 **disassembler**  
 A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive pipeline component that is invoked during the disassemble stage of inbound pipeline processing. A dissembler typically does the job of parsing an inbound message from some flat-file format into XML.  
  
## E  
 **error code**  
 A code, consisting of a letter followed by two digits, indicating a particular violation of the rules for a given message type.  
  
 **Extensible Markup Language (XML)**  
 A specification developed by the World Wide Web Consortium (W3C) that enables designers to create customized tags beyond the capabilities of standard HTML. While HTML uses only predefined tags to describe elements within the page, XML enables tags to be defined by the developer of the page. Tags for virtually any data item, such as a product or an amount due, can be used for specific applications. This enables Web pages to function as database records.  
  
 **Extensible Stylesheet Language (XSL)**  
 A style sheet format for Extensible Markup Language (XML) documents. XSL is used to define the display of XML in the same way that cascading style sheets (CSS) are used to define the display of Hypertext Markup Language (HTML). [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] uses XSL as the translation language between two specifications.  
  
## F  
 **FIN**  
 Financial messages for which SWIFT has defined schemas and validation standards in the SWIFT Standards Release Guide 2003.  
  
## G  
 **global assembly cache (GAC)**  
 A machine-wide code cache that stores assemblies specifically installed to be shared by many applications on the computer. Applications deployed in the global assembly cache must have a strong name.  
  
## H  
 **Hypertext Transfer Protocol Secure (HTTPS)**  
 Hypertext Transfer Protocol (HTTP) using the Secure Sockets Layer (SSL) encryption protocol.  
  
## I  
 **interchange**  
 A complete message made up of smaller message parts or blocks. For example, a SWIFT interchange in [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] is defined as the concatenation of a SWIFT header part (SWIFT blocks 1, 2, 3), followed by a SWIFT body part (SWIFT block 4), followed by a SWIFT trailer part (SWIFT block 5).  
  
## M  
 **map**  
 An XML file that defines the correspondence between the records and fields in one specification and the records and fields in another specification. A map contains an Extensible Stylesheet Language (XSL) style sheet that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] uses to perform the transformation described in the map. You create maps in BizTalk Mapper.  
  
 **message type**  
 One of the message formats defined in the SWIFT Standards Release Guide, such as "Receive Against Payment". Message types are often denoted by "MT" followed by a three-digit code.  
  
## P  
 **Payment Transaction Identifier (PTI)**  
 A unique transaction identifier, provided by the initiating customer, which is attached to payment-related banking messages originating from banks, such as Payment Initiation messages and Credit Advices.  
  
 **policy**  
 A versioned collection of business rules.  
  
 **PTI**  
 Payment Transaction Identifier.  
  
## R  
 **rule**  
 A pairing of conditions and actions.  
  
 **rule set**  
 A logical grouping of similar rules. This can be viewed as a grouping/partitioning mechanism of the rule engine.  
  
## S  
 **schema**  
 The definition of the structure of an XML file. A schema contains property information as it pertains to the records and fields within the structure.  
  
 **Society for Worldwide Interbank Financial Telecommunication (SWIFT)**  
 Society for Worldwide Interbank Financial Telecommunication. An organization that provides messaging services to banks, broker-dealers, investment managers, and market infrastructures in payments, treasury, securities, and trade. SWIFT creates a shared worldwide data processing and communications link and a common language for international financial transactions.  
  
 **specification**  
 A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]-specific XML schema. Specifications are created in BizTalk Editor and can be based on industry standards (such as SWIFT, EDIFACT, X12, and XML) or on flat files (delimited, positional, or delimited and positional). BizTalk Mapper uses specifications, opened as source specifications and destination specifications, to create maps.  
  
 **strong name**  
 A name that consists of an assembly's identity—its simple text name, version number, and culture information (if provided)—strengthened by a public key and a digital signature generated over the assembly. Because the assembly manifest contains file hashes for all the files that constitute the assembly implementation, it is sufficient to generate the digital signature over just the one file in the assembly that contains the assembly manifest. Assemblies with the same strong name are expected to be identical.  
  
 **Straight-Through Processing (STP)**  
 The automatic processing of a message over multiple steps, requiring no manual intervention. Usually applied to the processing path from reception of a message from SWIFT at a financial institution to the posting of the resultant transaction in the internal system(s) of the financial institution; or, from reception of an external instruction or action at a financial institution to the transmission of the resultant message(s) through SWIFT or other financial infrastructures; or, from an internal financial institution system to the transmission of one or more related messages through SWIFT or other financial infrastructures.  
  
 **SWIFT Standards Release Guides (SRG)**  
 The SWIFT publication that provides the updated and proposed standards for the set of FIN messages. This is a multi-volume set of documents defining the layout and fields for every message type, the valid values, and formats for each field, the network rules applied to each message, and any usage rules or common practices. This CD publication is available by subscription service from SWIFT.  
  
 **System Originated Message Trailer (SYS)**  
 A trailer appended by the SWIFT network to messages delivered to a financial institution, indicating that the FIN service generated the message. Examples are broadcasts, responses to user requests, and reports.  
  
## U  
 **Unique Remittance Identifier (URI)**  
 An identifier generated by participants in the RosettaNet Payments Milestone Program to synchronize banking interchanges with business interchanges.  
  
## X  
  
 **XML-Data Reduced (XDR)**  
 An early language used to create a schema, which identifies the structure and constraints of a particular XML document. XML-Data Reduced refers to the subset of the XML-Data schema specification that was made available in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] XML Parser (MSXML) 3.0 and later. It carries out the same basic tasks as DTD, but with more power and flexibility. Unlike DTD, which requires its own language and syntax, XDR uses XML syntax for its language. Unlike XSD, which has only recently been recommended as a standard, XDR was implemented and made available by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] well ahead of the existence of XSD as a recommended standard by the W3C XML Schema Working Group.  
  
 **XML Schema Definition (XSD)**  
 A language proposed by the W3C XML Schema Working Group for use in defining schemas. Schemas are useful for enforcing structure and/or constraining the types of data that can be used validly within other XML documents. XML Schema Definition refers to the fully specified and currently recommended standard for use in authoring XML schemas. Because the XSD specification was only recently finalized, support for it was only made available with the release of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] XML Core Services (MSXML) 4.0. It carries out the same basic tasks as DTD, but with more power and flexibility. Unlike DTD, which requires its own language and syntax, XSD uses XML syntax for its language. XSD closely resembles and extends the capabilities of XDR. The W3C now recommends the use of XSD as a standard for defining XML schemas.