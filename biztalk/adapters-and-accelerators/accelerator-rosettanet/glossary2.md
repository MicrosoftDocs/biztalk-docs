---
title: "Glossary for RosettaNet accelerator in BizTalk Server"
description: Common terms and definitions to know and learn to use the BizTalk Accelerator for RosettaNet
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: glossary
---
# Glossary
[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses the following glossary terms and definitions.  

  
## A  
 **application adapter**  
 An application that implements the application adapter interface. The notification mechanism on the acceptance of an incoming action message (request or response) invokes the application adapter. It implements two methods: `BeginNotify` and `EndNotify`. The public responder invokes the `BeginNotify` method, whereas the out-of-the-box private responder invokes the `EndNotify` method. The call to the `Notify` method means that the message was successfully saved into the MessagesToLOB table.  
  
 **action URL**  
 The partner URL to which the home organization transmits an action message during an asynchronous process, for example, http://FabrikamServer/BTARNApp/RNIFReceive.aspx.  
  
## B  
 **BizTalk Accelerator for RosettaNet**  
 An add-on product to BizTalk Server that helps organizations to build RosettaNet Implementation Framework (RNIF)-compliant solutions.  
  
 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Administration**  
 A Microsoft [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] application that lets you describe process templates and manage partner agreements.  
  
 **BizTalk Editor**  
 A tool with which you can create, edit, and manage specifications. With BizTalk Editor you can create a specification based on a specification template, an existing schema, certain types of document instances, or a blank specification.  
  
 **BizTalk Orchestration Designer**  
 A design tool you can use to create drawings that describe long running, loosely coupled, executable business processes. The XLANG schedule drawing is compiled in an XLANG schedule that you use to run the automated business process.  
  
 **BizTalk Server**  
 A Microsoft product for business-process automation and application integration both in and between businesses. BizTalk Server provides a powerful Web-based development and execution environment that integrates loosely coupled, long-running business processes, both in and between businesses.  
  
 BizTalk Server features include the composition of new and existing XLANG schedules; integration among existing applications; the definition of document specifications and specification transformations; and the monitoring and logging of run-time activity.  
  
 The server provides a standard gateway for sending and receiving documents across the Internet, and provides a range of services that help to ensure data integrity, delivery, security, and support for the BizTalk Framework and other key document formats.  
  
 **BtarnClean**  
 A utility to clean BTARN artifacts off a computer.  
  
 **business action**  
 A RosettaNet message that contains business content such as a purchase order request or a request for a quote. Together with business signals, these actions make up the necessary elements to complete the business activity specified by a particular Partner Interface Process (PIP).  
  
 **Business Activity Monitoring (BAM)**  
 A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] feature that gives business users a real-time view of their heterogeneous business processes. This enables them to make important business decisions.  
  
 **business signal**  
 A RosettaNet message, such as a ReceiptAcknowledgement or Exception, exchanged between two RosettaNet network applications to communicate certain events in the execution of a PIP instance. Together with business actions, these signals make up the necessary elements to complete the business activity specified by a particular PIP.  
 
  
## C  
 **CertWizard**  
 A utility to import a signing or encryption certificate from a .pfx (.p12) or .cer (.der) file into a private or public store for use with BTARN. A .pfx file, also known as Personal Information Exchange–PKCS #12, is typically protected by a password as it holds a private key that is used for decryption or signing. A .cer file (certificate file) holds the public key for encryption and validation of the signature.  
  
 **Chemical Data Exchange (CIDX) Chem eStandards**  
 Uniform standards of data exchange developed specifically for the buying, selling, and delivery of chemicals. These standards are based on the universally recognized standards for electronic data exchange—XML. BTARN supports CIDX Chem eStandards.  
  
 **cluster**  
 A group of high-level business processes, such as order management, inventory management, or service and support. The clusters addressed by RosettaNet represent core business processes for the supply chain industry.  
  
## D  
 **Data Universal Numbering System (D-U-N-S) number**  
 A sequentially generated nine-digit number that uniquely identifies business locations, and is global in scope.  
  
 **delivery header**  
 A part of a RosettaNet message. The delivery header is an XML document that identifies the message sender, the recipient, and message instance information.  
  
 **destination organization**  
 An organization that has been designated in a messaging port as the destination for documents.  
  
 **digital algorithms**  
 An algorithm that takes a message as input and produces a hash or digest of it, a fixed-length set of bits that depend on the message contents in some highly complex manner. Design criteria include making it extremely difficult for anyone to counterfeit a digest or to change a message without changing its digest. Applications that typically use digest algorithms are in message authentication and digital signature schemes. Widely used algorithms include MD5 and SHA1. BTARN supports both MD5 and SHA1 for incoming messages, and only SHA1 for outgoing messages.  
  
 **document definition**  
 A set of properties that represents a specific document. Document definition properties include a pointer to a document specification and can include global tracking fields and selection criteria.  
  
 **document instance**  
 A representation of the actual data that is sent to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. A document instance differs from a document specification in that the specification defines the structure of the data, while a document instance is a representation of the specific data that is contained in a structure.  
  
 **document type definition (DTD)**  
 A standard definition that specifies which elements and attributes might be present in other elements and attributes and that specifies any constraints on their ordering, frequency, and content.  
  
 **double action transaction**   
 A process where an initiator sends a request action, receives a signal, followed by a response action from the responder. The initiator finishes the process by sending a signal to the response action.  
  
## E  
 **Extensible Markup Language (XML)**  
 A specification developed by the World Wide Web Consortium (W3C) that enables designers to create customized tags beyond the capabilities of standard HTML. While HTML uses only predefined tags to describe elements in the page, XML enables tags to be defined by the developer of the page. Tags for virtually any data item, such as a product or an amount due, can be used for specific applications. This enables Web pages to function as database records.  
  
 **Extensible Stylesheet Language (XSL)**  
 A style sheet format for XML documents. XSL is used to define the display of XML just like cascading style sheets (CSS) are used to define the display of HTML. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] uses XSL as the translation language between two specifications.  
  
## G  
 **Global Business Identification (GBI)**  
 A unique identifier to identify trading parties. RosettaNet uses the nine-digit Dun and Bradstreet Numbering System (DUNS) as the GBI.  
  
## H  
 **home organization**   
 An alias to identify your organization.  
  
## I  
 **initiator**  
 The role of an organization in a transaction or notification process that initiates a process to a trading partner.  
  
## L  
 **Line of Business (LOB) Application**  
 The application that communicates with BTARN as the backend system.  
  
 **Loopback utility**  
 A utility for developers to automatically generate a loopback agreement that is a mirror copy of a home-to-partner agreement. This lets you perform home-to-partner and partner-to-home message exchanges on a single computer.  
  
## M  
 **map**  
 An XML file that defines the correspondence between the records and fields in one specification and the records and fields in another specification. A map contains an XSL style sheet that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] uses to perform the transformation described in the map. Maps are created in BizTalk Mapper.
  
 **my organization**  
 Represents your organization in a trading partner agreement.   
  
 **Multi-Purpose Internet Mail Extensions (MIME)**  
 An extension of the Internet e-mail protocol that lets you use the protocol to exchange different kinds of data files on the Internet: audio, video, images, and application programs.  
  
## N  
 **non-repudiation**  
 A way to make sure that the sender of a message cannot later refuse to recognize that the sender sent the message and that the recipient cannot deny having received the message. Non-repudiation of an incoming message requires that the message be saved by the receiver, and that the message should carry a digital signature using the signing certificate of the sender to ensure its authenticity. Non-repudiation of an outgoing message requires saving the acknowledgement message (incoming message from the recipient of the first message), and that the message should carry the digital signature of the digest of the original message using the signing certificate of the recipient.   
  
 **notification**  
 An RNIF 1.1 process type where the initiator notifies the responder with a single message. The responder is expected to reply with a business signal as an acknowledgement.  
  
 **Notification of Failure (PIP 0A1)**  
 A special PIP that indicates unexpected process failures. The initiator or the responder can initiate a Notification of Failure. It refers to an existing or previously exchanged process. Upon receipt of a 0A1, the receiving party makes sure that the referenced process is considered not valid.  
  
## O  
 **organization**  
 A trading partner or a business unit that can conduct business transactions.  
  
## P  
 **packaging**  
 The process of converting a RosettaNet message in its XML representation and vice versa.  
  
 **Partner Interface Process (PIP)**  
 A PIP describes a set of business documents and agreement details, including document content details.  
  
 **PIP Specification document**  
 A document that contains guidance about the settings to use when you create a process configuration in the BTARN Management Console. You download the PIP Specification document and the PIP from the RosettaNet organization, from RosettaNet.org. A document that contains guidance about the settings to use when you create a process configuration in the BTARN Management Console. You download the PIP Specification document and the PIP from the RosettaNet organization, from RosettaNet.org.  
  
 **preamble header**  
 An XML node that identifies the name and version of the standard with which a business message is compliant. It is packaged together with other headers to form a complete RosettaNet Message. Also named preamble.  
  
 **private process**   
 Business processes that are internal to an organization. BTARN implements private processes as long-running BizTalk orchestrations.  
  
 **Process Configuration Setting (PCS) profile**  
 Determines how a partner agreement runs. You use the PCS profile to enter the configuration details of a RosettaNet Partner Interface Process (PIP). All configuration values specified in a RosettaNet PIP specification map to one element in the PCS profile. You can use one PCS profile for multiple partner agreements.  
  
 **port**  
 A named location that uses a specific implementation. In BizTalk Orchestration Designer, a port is defined by the location to which messages are sent or from which messages are received, and the technology that is used to implement the communication action. The location is uniquely identified by the name of the port.  
  
 **public process**   
 Business processes that involve integration with trading partners as public processes. BTARN implements public processes as long-running BizTalk orchestrations. One public-process orchestration runs on the initiator side and one on the responder side. The BTARN Setup program provides versions of the initiator and responder public-process orchestrations for both RNIF 1.1 and RNIF 2.01. These public-process orchestrations implement all RNIF processes. Public processes hide the complexity of RNIF from the rest of the components. Besides enforcing the RNIF-compliant message flow, the public process also determines default-tracking settings and provides process state information at runtime.  
  
## R  
 **responder**  
 The role of an organization in a transaction or notification process that responds to a request by a trading partner.  
  
 **RosettaNet Implementation Framework (RNIF)**  
 A standards framework that provides implementation guidelines for those companies that want to create interoperable software application components that run PIPs.  
  
 **RosettaNet message**  
 The logical grouping of the preamble header, delivery header (in the case of RNIF 2.0), service header, and service content.  
  
 **RosettaNet object**  
 A RosettaNet message enveloped for delivery in RosettaNet Implementation Framework version 1.1.  
  
## S  
 **schema**  
 The definition of the structure of an XML file. A schema contains property information as it pertains to the records and fields in the structure.  
  
 **service content**  
 The primary component of the RosettaNet message. It is an XML node that represents the business content specified by a particular PIP.  
  
 **service header**  
 An XML document that identifies the parts associated with a business message, including the PIP, business activity and action, sending and receiving services, trading partners, and roles.  
  
 **signal URL**  
 The URL to which the home organization transmits a signal message. For example, http://FabrikamServer/BTARNApp/RNIFReceive.aspx.  
  
 **single action notification**  
 A process where the initiator sends a single action message and the responder replies with a message.  
  
 **specification**  
 A [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]-specific XML schema. You create specifications in BizTalk Editor and can be based on industry standards, such as EDIFACT, X12, and XML, or on flat files, such as delimited, positional, or delimited and positional. BizTalk Mapper uses specifications, opened as source specifications and destination specifications, to create maps.  
  
 **sync URL**  
 The URL that the home organization uses to establish synchronous transactions with the partner, for example, http://FabikamServer/BTARNApp/RNIFReceive.aspx.  
  
 **synchronous transaction**  
 A process where the initiator returns a response (double-action) or signal (single-action) on the same HTTP state without closing the connection.  
  
## T  
 **trading partner**  
 An external organization with which your organization exchanges electronic data.  
  
 **trading partner agreement**  
 An agreement between your organization and your trading partner. A trading partner agreement references a Process Configuration Setting profile, home organization, partner, and contains agreement specific configuration settings.  
  
 **transaction**  
 An RNIF 1.1 process where the initiator sends a RosettaNet message, receives a signal, receives a RosettaNet message as an answer, and sends a signal for acknowledgement.  
  
## V  
 **validation adapter**  
 An application that implements the Validation Adapter interface. The public responder invokes the Validation Adapter when it receives an action message (request or response). It can include any set of validation rules that a business may require before accepting an incoming message. BTARN natively performs validation in the receive pipeline, and in public orchestrations.  
  
## X  
 **XLANG schedule**  
 A specific XML language that describes business processes and back-end integration. Specific business processes in BTARN are expressed in the XLANG language. An XLANG schedule is saved with the file name extension .skx.  
  
