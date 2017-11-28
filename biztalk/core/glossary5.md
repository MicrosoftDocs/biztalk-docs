---
title: "Common terms and definitions | Microsoft Docs"
description: Glossary of terms and and their meanings for BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac9c7c7d-a97e-425a-9666-02ca6edd8be6
caps.latest.revision: 68
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Glossary
The following terms and definitions are used in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
## .  
  
|Term|Definition|  
|----------|----------------|  
|.brl file|A business rules definition file.|  
|.btm file|A BizTalk Server map file.|  
|.btp file|A BizTalk Server pipeline file.|  
|.btproj|A BizTalk project file.|  
|.btt file|A tracking profile file.|  
|.odx file|A BizTalk Server orchestration file.|  
|.xsd file|A BizTalk Server schema file.|  
|||  
  
## A  
  
|Term|Definition|  
|----------|----------------|  
|action|One or more functions corresponding to the "THEN" part of a rule and used to specify what is to be done when a condition evaluates to true.|  
|Activate property|A property of the Receive shape, used to indicate that the orchestration is activated when a message is received. The Receive shape can only be marked as activated if it is the first send- or receive-activated shape in an orchestration.|  
|activation block|A grouping of steps or actions within an activity model.|  
|activation receive|A shorthand expression for the condition of the Receive shape when the Activate property on this shape is set to True.|  
|activity model|A predefined sequence of actions. These can be invoked in activation blocks.|  
|activity model step|A synonym for an action from the viewpoint of an activity model. When an action is contained within an activity model, it is referred to as an activity model step.|  
|activity node|A node that contains the milestones and data items that represent the data of interest to the business analyst, which the analyst creates using Microsoft Excel wizards.|  
|activity window|Defines the time period over which activity instance data is visible. The data is always changing because the point in time is always changing. After the data passes through the activity window you can move it to the BAM Archive database by running the Data Maintenance DTS/SSIS package. After you move it to the BAM Archive database, it is no longer available for queries on the BAM portal.|  
|actor|A person or process that either starts or participates in an activity. Actors can be either initiators or targets.|  
|adapter|A COM or .NET-based component that helps exchange messages between applications (for example, a line-of-business system) and BizTalk Server. The adapter consists of design-time components and run-time components for receive and send operations.|  
|adapter framework|The specifications for building BizTalk adapters using open standards based on Web Services.|  
|addendum|A piece of an agreement. An agreement consists of multiple addendums that define the business process that is used, your role, your partner’s role, and the policies or parameters that are used in that relationship along with documentation, such as a list of business and legal terms.|  
|affiliate application|A logical entity in Enterprise Single Sign-On (SSO), defined by the administrator, that represents a system or subsystem such as a host, back-end system, or line-of-business application to which you are connecting using SSO. An affiliate application can represent a non-Windows system such as a mainframe or UNIX computer. It can also represent an application such as SAP, or a subdivision of the system, such as the "Benefits" or "Pay stub" sub-systems.|  
|agenda|An ordered list of rule actions to be executed by the Rule Engine.|  
|aggregation|A table or structure containing pre-calculated data for an online analytical processing (OLAP) cube. Aggregations support the rapid and efficient querying of a multidimensional database.|  
|agreement|The defining item in relationship configuration. An agreement is based on the underlying business process and party management artifacts, and is defined between your self profile and your partner’s profile. It consists of one or more addendums. Addendums define the business process used, the role of your organization, your partner’s role, and the parameters used in the relationship. Agreements can also refer to partner group profiles instead of individual partner profiles. This facilitates the management of partners that have identical trading relationships with your organization.|  
|alert notification|The means used to notify a user or a group of users about a specific predefined situation that could manifest.|  
|alias|A alternate way to refer to a party. Each party is given a single default alias with a name of organization, a qualifier as OrganizationName, and value for the name of the party. This alias is always regarded as the default alias. Aliases are provided as triads of name, qualifier, and value. No two parties in the same BizTalk Management database can have the same qualifier value pair.|  
|All, FirstMatch|Two types of execution modes for pipeline stages. All indicates the linear execution of pipeline components in the stage. FirstMatch indicates a probed execution in which the first component that recognizes the message format consumes the message. In linear execution, all components in a stage are executed in order before the message is passed to the next stage.|  
|ANSI X.12|A message format developed by the American National Standards Institute. X.12 is used primarily in the United States.|  
|application adapter|An adapter created to work with a specific application or protocol, such as SQL.|  
|archived data|Data that has been processed by BizTalk Server and stored in the appropriate database.|  
|artifact|Most often referred to as a part of a BizTalk application, which is a logical unit for a BizTalk solution. Artifacts are managed and deployed through the BizTalk Administration console. Examples are orchestrations, pipelines, message schemas, security certificates, business rule policies, and bindings. Artifacts are also the parts of a BizTalk project, another logical unit for a BizTalk solution. In this context, the artifacts are used to generate the assemblies in Visual Studio that make up the BizTalk solution.|  
|assembler|A pipeline component that combines individual documents into a batch. Assembler pipeline components provided in BizTalk Server are Flat file assembler, BizTalk Framework Assembler, and XML Assembler pipeline components.|  
|assembly|A dll file that may contain resources, such as orchestrations, pipelines, schemas, maps, and other resources that are not BizTalk Server specific, to be used in a BizTalk application.|  
|assembly deployment|The process of deploying the resources of an assembly from Visual Studio into a BizTalk application.|  
|Assembly Deployment Wizard|In BizTalk Server 2004, a wizard that guided you through the steps required to add, remove, import and export assemblies; import and export bindings; and install or uninstall assemblies from the global assembly cache (GAC). In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], this functionality is not provided by the Import, Installation, and Export Wizards.|  
|assembly version|An identifier for an assembly, made up of a combination of a major and a minor version.|  
|atomic orchestration|A short-lived transaction that enforces the commit and rollback semantics of an ACID (Atomicity, Consistency, Isolation, and Durability) transaction similar to a COM+ application that uses the DTC service.|  
|attribute|In XML, an XML construct used to associate additional information with XML elements.|  
|Authentication Trusted|A means of marking each application indicating that the application can submit messages into the message box with a Party ID (PID) that is different (that is, not aliased by) the Windows Security ID of the application instance service account.|  
  
## B  
  
|Term|Definition|  
|----------|----------------|  
|BAM|See Business Activity Monitoring (BAM).|  
|BAM activity|The end-to-end list of milestones and data captured by BAM for a unit of work to be monitored. For example, a loan application activity might contain milestones such as “Loan approved” and data such as “Applicant name” and “Loan amount.” BAM activities often map directly to a business process.|  
|BAM alert|A notification generated by the BAM infrastructure (specifically, by SQL Server Notification Services) to inform the recipient that a given set of conditions exists. Users define the conditions for an alert and then automated services generate the alert whenever those conditions are met.|  
|BAM checkpoint|Also known as an item in the BAM Add-in for Excel.|  
|BAM Configuration|The XML file that contains the settings for BAM manifests such as the BAM Primary Import database and server names.|  
|BAM definition|An XML representation of a BAM observation model.|  
|BAM Framework|A set of managed APIs that support dynamically created infrastructure and event concentration.|  
|BAM infrastructure|Consists of SQL Server tables, BAM views, stored procedures, and Data Transformation Services (DTS) packages in the BAM databases (Primary Import, Archive, Star Schema, and Analysis) as configured and managed through incremental deployments of BAM definitions. The infrastructure is where, at run time, events are correlated, aggregated, and then made available for user queries.|  
|BAM Manager|The internal component that manages the dynamic infrastructure for Business Activity Monitoring.|  
|BAM observational model|A high-level definition of visibility requirements for a business process that specifics the milestone and data events to collect (the BAM activity); a description of any data aggregations; and the presentation of information to users (the BAM view).|  
|BAM view|A role-specific perspective on the data that constitutes a BAM activity. Views consist of filtered data, aggregations of the filtered data, and ways of presenting the filtered data, such as a PivotChart report. BAM supports the definition of one or more views per activity.|  
|base data item|In BAM, an Activity item that is used as a basis for a dimension or measure. For example, the base data item  "product ID" could be used as the basis for a Count measure (how many of a given product was sold).|  
|binding|A process by which software components and layers are linked together. When a network component is installed, the binding relationships and dependencies for the components are established. Binding allows components to communicate with each other. In BizTalk Server, an established mapping between an orchestration adapter-agnostic endpoint (port or role link) and physical adapter-specific endpoints (send/receive ports or party).|  
|binding file|A file that contains a snapshot of the binding as seen at that instant. It does not contain details about the completeness of the binding with respect to the orchestration.|  
|BizTalk Administration console|A Microsoft Management Console (MMC) used to administer a BizTalk Server group.|  
|BizTalk Administrators group|The group that administers BizTalk Server. Administrative tasks include accessing the Suspended queue, updating the Configuration database, and so on.|  
|BizTalk application|A group of related artifacts, resources, and settings that are exposed together for management from within the BizTalk Administration console. Any artifact within an application may refer to any other artifact within that application, as well as any artifact in any referenced application.|  
|BizTalk Application 1|The application created by default in every new BizTalk Server installation. This application is created mainly for backwards compatibility. Artifacts that were deployed without an application specified are shown in this folder. Also, new artifacts that are deployed without an application specified are deployed to the Default Application. Any other application may be set as the default by changing a user setting.|  
|BizTalk Application Users group|The group of users who can access MessageBoxes for a particular BizTalk Group|  
|BizTalk Application view|One of two views (along with BizTalk Deployment View) that appears when the System Center Operations Manager console for BizTalk Server is opened. A BizTalk administrator uses this view to monitor the health of BizTalk artifacts and applications such as orchestrations, send ports, and receive locations.|  
|BizTalk assembly|A Microsoft Windows DLL  file that contains resource information, such as orchestrations, pipelines, schemas, and maps to be used in a BizTalk Server business solution. The assembly also contains the version number, the culture, and public key tokens.|  
|BizTalk Deployment view|One of two views (along with BizTalk Application view) that appears when the System Center Operations Manager console for BizTalk Server is opened. An enterprise IT administrator uses this view to monitor the overall health of the “physical deployment” of a BizTalk Server setup.|  
|BizTalk Editor|A visual tool, hosted within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], for constructing BizTalk Server schemas that can define the structure of both XML- and native-formatted instance messages.|  
|BizTalk Explorer|A Visual Studio tool window that displays the contents of a BizTalk Configuration database. It displays items such as assemblies, ports, and parties in a hierarchical tree. You can use BizTalk Explorer to configure and manage BizTalk projects, parties, and orchestrations.|  
|BizTalk Explorer Object Model|The APIs used to create tools and scripts to automate the post-deployment tasks that you perform in BizTalk Explorer. You can use the BizTalk Explorer Object Model for such post-deployment tasks as creating ports, binding orchestrations, managing party properties, or any other task where you would use BizTalk Explorer. The BizTalk Explorer Object Model APIs are in the Microsoft.BizTalk.ExplorerOM namespace.|  
|BizTalk Framework|A platform-neutral e-commerce framework that is based on Extensible Markup Language (XML) schemas and industry standards. The framework enables integration across industries and between business systems, regardless of platform, operating system, or underlying technology.|  
|BizTalk group|A group that contains MessageBoxes, hosts, receive locations, send ports, send port groups, orchestrations, servers, and adapters.|  
|BizTalk host|A logical process and security boundary within BizTalk Server. Each host has a security group assigned to it and may contain multiple host instances, each on an individual machine, that perform the work of the host. In turn, each host instance belongs to exactly one host, and the service account of the host instance belongs to the security group of the host. The security group may be used to grant permissions to physical resources such as databases for use by any host instances in the host.|  
|BizTalk Management Pack alert|A notification that administrators can subscribe to in the BizTalk Server Management Pack. After subscribing to a given alert, administrators receive a notification whenever certain conditions are met. For instance, if a certain number of host instances are throttling, an alert could be raised.|  
|BizTalk Management Pack diagnostics|A feature that administrators can use to see the cause and troubleshooting information for a given problem. For example, if the health of a send port appears as red, the State Change Event tab in the Operations Manager console displays the reason why it went from green to red.|  
|BizTalk Mapper|A visual tool, hosted within Visual Studio, for constructing BizTalk maps, which define data transformations.|  
|BizTalk Message Queuing|The message queuing transport component in BizTalk Server. It is shipped as a core internal component of the BizTalk Server product and is one of many adapter components in BizTalk Server.|  
|BizTalk message store|A Microsoft SQL Server table that holds all messages and their parts. Consuming orchestrations use the message references contained in the store to dequeue a copy of the message and its properties from the message store.|  
|BizTalk project|A type of Visual Studio project used to create applications that run on BizTalk Server.|  
|BizTalk project file (.btproj)|A file that contains project-specific settings for a BizTalk project.|  
|BizTalk project system|A system used to create part or all of a BizTalk Server application or business solution. You use it to add, edit, or remove BizTalk Server items (orchestrations, maps, schemas, and pipelines). It contains commands such as compile and deploy.|  
|BizTalk Server Management Pack|A BizTalk enhancement that helps ensure full monitoring capabilities of BizTalk applications and infrastructure. It includes features like diagnostics and alerts to help monitor the health of a BizTalk deployment.|  
|BizTalk Server Administration|A Microsoft Management Console (MMC) interface that is used to administer the BizTalk Server group of servers and their properties, to monitor receive functions, and to monitor work items in the Microsoft SQL Server queues that are used by the server group.|  
|BizTalk Server map file (.btm)|The persisted form of a BizTalk map, created by BizTalk Mapper and compiled to generate run-time transformation directives specified using Extensible Stylesheet Language Transformations (XSLT).|  
|BizTalk Mapper|A feature that visually enables users to build transformations between two schemas in a BizTalk application. It also has usability enhancements to help with complex maps.|  
|BizTalk Server Messaging Engine|A set of services required in a middleware product to facilitate solutions to customer scenarios. These run-time services are an essential part of the BizTalk Server platform. Among these services are performant pipeline processing of messages. Pipeline processing provides data format normalization and property extraction.|  
|BizTalk Server pipeline file (.btp)|A file that describes the configuration of the pipeline and the components within it. This file type can be compiled as part of a BizTalk project.|  
|BizTalk Server schema|An XML Schema Definition language (XSD)-based description of the structure of one or more BizTalk Server instance messages.|  
|BizTalk Server schema file (.xsd)|A file containing the persisted form of a BizTalk schema.|  
|BizTalk Settings Dashboard|A BizTalk feature that BizTalk administrators can use to centrally manage and modify BizTalk Engine settings. Administrators can export and import settings from one environment to another, such as from staging to production.|  
|body part|See message body part.|  
|BTSTask|A command-line tool that enables you to manage applications and assemblies. You can use BTSTask to add a BizTalk application to the BizTalk Management database, add a resource to an application, export an application to an MSI file, export binding information to a file, import an application from an MSI file, import binding information from a file, list all of the resourcesin an application, list all applications in the BizTalk Management database, list the contents of an MSI file, remove an application from the BizTalk Management database and BizTalk Administration Console, and remove a resource from an application.|  
|Business Activity Monitoring (BAM)|A BizTalk Server feature that gives business users a real-time view of their heterogeneous business processes, enabling them to make important business decisions.|  
|Business Activity view|A hierarchical set of views that show a business process or processes, used to define the way a specific category of business users want to see the business activity. There may be more than one way of interpreting the same business activity data (BAM Traces).|  
|business analyst|A user who possesses business management and economics analysis skills. The primary responsibility of the business analyst is to consume business-level data and analyze it for business trends.|  
|business end user|An information worker who has responsibility for monitoring and troubleshooting a business process and/or exchange of business messages. This person in not technical.|  
|Business Process Configuration services|Tools that enable business users to configure and manage lower level orchestration items using business policies. Developers or ISVs use these tools to define business processes so that they can be configured using business policies and parameters.|  
|Business Process Workspace|An interface that enables business managers to track and manage all the business processes from SharePoint Team Services.|  
|business profile|The business face of an organization. Each business division in an organization that trades with another business division in another organization is represented as a business profile in a trading partner management (TPM) solution. All properties that define the business-to-business messaging parameters specific to the business division, business unit, or business system are captured in its business profile.|  
|Business Rule Composer tool|A graphical user interface tool used to compose policies.|  
|Business Rule Engine|A run-time inference engine that evaluates rules against facts and initiates actions based on the results of that evaluation.|  
|Business Rule Language|A rule markup language in XML format for declarative rule definitions.|  
|business-to-business|Relating to the sales category pertaining to transactions and related activity between a business and buyers who are not consumers, such as government bodies, companies, and resellers. Refers to one business communicating with or selling to another.|  
  
## C  
  
|Term|Definition|  
|----------|----------------|  
|calculated duration|A property that enables the use of a custom formula for calculated columns.|  
|code list|A set of abbreviation/explanation pairs that are used as a design-time aid to providing sets of XML Schema Definition language (XSD) enumeration values.|  
|command-line deployment tool|Tools used to add, remove, import and export assemblies, import and export bindings, and install or uninstall assemblies from the global assembly cache (GAC).|  
|commit change request|See Other Term: end type change request|  
|communication pattern|A property that determines whether the communication on the port is one-way or two-way (request-response).|  
|compensation|A group of actions designed to undo or mitigate the effect of a committed transaction.|  
|Compensation tab|A design surface used for adding compensation to an orchestration.|  
|compile|In the context of BizTalk Server, the process of converting the design-time representation of BizTalk Server items such as schemas, maps, and orchestrations into their run-time equivalents, stored in Visual Studio assemblies.|  
|Composition service|The component that handles the action activation, interrupt functionality, and the sending of task responses. The service composes the action protocol messages and sends them to the HTTP listeners which then rout them into the MessageBox database for consumption.|  
|condition|The "IF" part of a rule, used to specify what conditions should be evaluated, that is, represented using a single logical expression that evaluates to true or false. A condition is extensible to support user-defined conditions.|  
|configuration cache refresh Interval|The interval, in seconds,  in which changes to general properties for a BizTalk group, such as the SMTP host, are picked up.). This interval is set as part of group configuration. When you start BizTalk Server, all items in BizTalk Server Administration, such as MessageBox databases, server properties, adapters, and connections to the Tracking database, are stored in the administration cache. By default, all items in the cache are refreshed every 60 seconds, except for the server database connections and server properties.|  
|Configuration database server name|A UI element. The name of the server on which the Management, or configuration, database is housed.|  
|connector|A communications service used to exchange documents with your trading partners or your internal systems.|  
|connector point|An element in the Orchestration Designer that enables users to connect a Send/Receive shape with the operation of a port.|  
|constraint|A property that restricts the initiator of the root action and targets for any other action within the activity model.|  
|content-based routing|The routing of a document based on the information extracted from the payload of the document. In BizTalk Server, content-based routing is achieved by using document property promotion and filter expressions on send ports and orchestrations.|  
|continuation|The ability to contribute to a single BAM activity from different applications by using two different unique identifiers as the ActivityID. For example, in one part of a business process, a customer’s PO number might be used to track an activity. In another part of the process, an internal order fulfillment number might be used to track the same activity. You could enable continuation and relate the PO number and the order fulfillment number, so that both parts of the process could add information to the same activity.|  
|Continuation token|A piece of unique information that is sent out of Application 1.|  
|conversion rate|The multiplier used for converting the base currency of the Web site to the buyer currency or supplier currency. The conversion rate is stored in the SDK Order Sitelet for illustrative purposes only, and should be tracked by a third party fulfillment or accounting system in production Web sites.|  
|correlation|The process of matching an incoming message with the appropriate instance of an orchestration. This matching occurs through properties of the message that link it to the orchestration. In cases where messages related to the same business process contain incompatible properties, such as a purchase order schema with an element POId, and a companion invoice schema with an element OrderID, developers achieve the correlation by creating property schemas that contain abstracted property names for these elements.|  
|correlation ID|A randomly generated ID that is associated with a message and passed along for the lifetime of a given message.|  
|correlation set|An instance of a correlation type; that is, the listed properties for a message that are used to determine whether it belongs to a given instance of an orchestration.|  
|correlation type|A set of message properties that uniquely identify a business process and that are used to correlate messages with orchestration instances.|  
|culture|The language and localizable properties of text and data.|  
|custom adapter|A custom piece of code that a developer writes and places before a receive pipeline or after a send pipeline to interface with adapters and/or applications.|  
|custom numbers|A series of numbers assigned by a counter that increases the value of each number by one.|  
|cyclical reference|A pattern in an XML schema in which a descendant node is declared to be of the same complex type as one of its ancestor nodes, thereby creating a schema that represents instance messages with potentially unlimited depth.|  
  
## D  
  
|Term|Definition|  
|----------|----------------|  
|Data Description Language (DDL)|A language used to define data and its relationships to other data. It is used to create the data structure in a database. Major database management systems (DBMSs) use a SQL data description language.|  
|data dimension|A specific node created in the hierarchical view of the Tracking Profile Editor as an immediate child of the specific tracking profile in order to describe a logical grouping or dimension of data. Each data dimension is uniquely named and is made up of one or many data fields.|  
|data item|A specific node created in the hierarchical view of the Tracking Profile Editor that is a direct child of Data Category. The data field exists as a specific field from the business payload.|  
|data mapping|The design-time process of defining a mapping between nodes in a source schema and nodes in a destination schema.|  
|DDL|See Data Description Language.|  
|default host|Administration objects that facilitate deployment and orchestration enlistment. These objects are identified in the BizTalk Server Administration console with a checkmark symbol. During the orchestration enlistment process, the default host is automatically used to host the orchestration, unless the user explicitly selects a different host.|  
|default pipelines|The compiled and deployed BizTalk Server assemblies that contain pipelines with preconfigured stages and pipeline components.|  
|dehydrate|Saving the state of a running orchestration to persistent storage and removing it from memory when the orchestration has been idle for a certain length of time.|  
|delimited flat file|A type of file format used to represent business documents in which the records and fields within the records are delimited by specific characters or sequence of characters.|  
|delimiter|One or more special characters that are used to separate peers in a delimited structure, at any level (fields, records, and so on).|  
|demotion|The act of writing date/time data from a context property into the document payload.|  
|Destination database|When installed with BizTalk Server, the only destination that is supported, although multiple Destination databases are supported by the BAM Event Bus Service infrastructure.|  
|destination schema|The schema used in a BizTalk Server map that represents the structure of the output message instances.|  
|Development Tools Environment (DTE)|A set of interfaces that enable developers to programmatically achieve several of the key tasks achievable from the Integrated Development Environment (IDE).|  
|dimension hierarchy|A logical tree structure that organizes the members of a dimension such that each member has one parent member and zero or more child members.|  
|dimension level|An element that indicates that a set of data items are to be considered as levels of a dimension hierarchy. The DataPerspective definition results in an OLAP Dimension Hierarchy.|  
|disassembler pipeline component|A pipeline component that divides messages in a batch into individual documents. The disassembler pipeline components provided in BizTalk Server are: Flat file disassembler, BizTalk Framework disassembler, and XML disassembler.|  
|distinguished field|A .NET class member or XML Schema Definition language (XSD) schema field in a message that has been explicitly made available to an orchestration for use in expressions and custom pipeline components as a written property field. It cannot be used in filter expressions.|  
|distributed transaction coordinator (DTC)|A service, integrated with COM+, that makes distributed transactions work.  DTC makes it possible to scale transactions from one to many computers without the need for special code.|  
|DMZ|Demilitarized zone. See perimeter network.|  
|document|In EDI, a set of logically combined segments. Types of documents include: invoices, transportation orders, customs declarations, and so on.|  
|document type definition (DTD)|One of several ways in which the structure of an XML document can be described. BizTalk Server can open a schema described using a DTD, but converts it to XSD in the process.|  
|DTC|See distributed transaction coordinator (DTC).|  
|DTD|See document type definition (DTD).|  
|DTE|See Development Tools Environment (DTE).|  
|duration|An element that instructs the BAM Compiler to create additional column in the View that represents the duration between checkpoints.|  
|dynamic adapter|An adapter that has a custom user interface.|  
|dynamic binding|A port binding that is applied to the port at run time, typically derived from a message property such as a reply-to address.|  
|dynamic policy update|The run-time retrieval of policies using the Rule Engine Update service.|  
|dynamic port|A send port that does not have a destination address and adapter type associated with it. A dynamic send port allows the association of the destination address and adapter type with itself during runtime execution, thus providing flexibility in using the same port for sending messages to different destinations using different adapter types.|  
  
## E  
  
|Term|Definition|  
|----------|----------------|  
|EDI|See electronic data interchange (EDI).|  
|EDIFACT|See Electronic Data Interchange for Administration, Commerce and Trade (EDIFACT).|  
|EDIFACT UNOA syntax|An EDIFACT syntax that allows the following characters only: uppercase letters, all digits, blank, exclamation mark (!), quotation mark ("), percentage sign (%), ampersand (&), opening and closing parentheses ( "(" and ")"), asterisk (*), comma, dash (-), decimal point (.), forward slash (/), semicolon (;), less-than sign (\<), and greater-than sign (\>).|  
|EDIFACT UNOB syntax|An EDIFACT syntax that allows the following characters only: lowercase and uppercase letters, all digits, blank, exclamation mark (!), quotation mark ("), percentage sign (%), ampersand (&), single quotation mark ('), opening and closing parentheses ( "(" and ")"), asterisk (*), plus sign (+), comma, dash (-), decimal point (.), forward slash (/), colon (:), semicolon (;), less-than sign (\<), equal sign (=), greater-than sign (\>), and question mark (?).|  
|EIF|See Engine Input File (EIF).|  
|EIP|See Enterprise Integration Platform (EIP).|  
|electronic data interchange (EDI)|The electronic exchange of structured and normalized documents between two computer applications, using a set of standards to control the transfer of documents, such as purchase orders and invoices, between computers.|  
|Electronic Data Interchange for Administration, Commerce and Trade (EDIFACT)|A worldwide electronic data interchange (EDI)|  
|element|In EDI, the lowest level of information in a document. For example, invoice number. In XML, an XML construct used to organize information in a hierarchical manner by nesting some elements within other elements to a potentially unlimited depth.|  
|element groups|Groupings of sibling elements in an XML structure according to different constraints: ordered sequence (Sequence Group), unordered sequence (All Group), and one-of-many (Choice Group).|  
|encoding agreement|An agreement between the business profiles of two trading partners to use a specific encoding protocol (X12 or EDIFACT) while exchanging messages.|  
|encoding protocol|A protocol that governs the structure and content of a business-to-business message. The encoding protocol settings for a business profile define the encoding protocol that a business division uses to send and receive business-to-business messages. Some examples of encoding protocols are X12, EDIFACT, HIPAA, and EANCOM.|  
|encryption key|A string used to encrypt or decrypt credentials information.|  
|end type change request|The last stage of the deployment of an artifact type onto the destination computer, during an import of a BizTalk application MSI file using the Administration console or BTSTask. Also known as a commit change request, or commit import for a type of artifact.|  
|endpoint|The logical representation of a location, typically expressed in URL form, providing a physical address for data received or sent.|  
|Engine Input File (EIF)|A compiled version of a document schema. The EIF is used to expedite translations for distribution among other users in a closed user group. The EIF is automatically compiled whenever an XML Schema Definition language (XSD) schema is generated or edited, using BizTalk Server.|  
|enlist|The process of associating an orchestration with the physical environment in which it will run. This includes specifying  the adapters needed to transport messages to and from the orchestration, the application process in which the orchestration is hosted, and creating the MessageBox subscriptions indicated by the routing.|  
|enterprise application integration|The process of bringing data or a function from an enterprise application together with that of another application.|  
|Enterprise Integration Platform (EIP)|The environment in which enterprise application integration occurs. This scenario is actually a class of scenarios grouped together as a single scenario.|  
|Enterprise Single Sign-On system|An SSO database, a master secret server, and one or more Enterprise Single Sign-On (SSO) servers. These servers do the mapping between the Windows and non-Windows credentials, look up the credentials in the SSO database, and are used for administering the SSO system. The SSO database is also used as a configuration store to hold custom configuration data for adapters.|  
|envelope|A structured set of information that wraps and accompanies an instance message, often describing delivery and processing information. Envelopes can be nested.|  
|envelope schema|A type of schema that specifies the structure of an envelope, using several extra properties that are specific to envelopes and which specify information such as identifying the envelope contents in an enveloped data stream.|  
|execution cycle|The assertion of facts, evaluation of conditions, and execution of actions within the Business Rule Engine.|  
|Execution Mode|A pipeline stage property that determines the execution pattern of pipeline components in a stage. The Execution Mode can be set to All or First Match. In All mode, all the components within the stage are carried out in the configured sequence. This mode is used when several components are required to complete a certain logical task, and they must all be executed. If any component encounters an error while processing a message that is going through this pipeline stage, a run-time error results.|  
|Export Wizard|A wizard that you start from the BizTalk Administration Console to generate an MSI file from a BizTalk application. You can then copy this MSI file to a different instance of BizTalk Server and use the Import Wizard to import the resources of the MSI file.|  
|express delivery|A type of message delivery that implies persistency (store in the SQL database), both for incoming messages and outgoing messages.|  
|Extensible Stylesheet Language Transformations (XSLT)|Evolved from the early Extensible Stylesheet Language (XSL) standard. XSL specifies a language definition for XML data presentation and data transformations. Data presentation means displaying data in some format and/or medium, and concerns style. Data transformation refers to parsing an input XML document into a tree of nodes, and then converting the source tree into a result tree. Transformation concerns data exchange.|  
|external message format|The format of the message before or after it is processed by BizTalk Server. Sometimes the term "wire" format is also used when referring to external message format.|  
  
## F  
  
|Term|Definition|  
|----------|----------------|  
|facet|An XML Schema Definition language (XSD) concept for restricting the possible values that an element or attribute can take, providing validation parameters for instances of a schema. For example, a minimum and maximum length can be specified for string data. Different types of facets apply to different types of data.|  
|fact|User data to which rule conditions are applied. At design time a fact is a reference to that data.|  
|fact base|A collection of facts against which rule conditions are evaluated.|  
|fact retriever (Rule Engine)|An optional, user-defined plug-in component that implements an IFactRetriever interface so that it can gather long-term facts for use by business policies.|  
|fact store|The database that stores information, including role and attributes, about actors. The fact store also provides hierarchy navigation so that actions can determine the relative positions of actors within an organization.|  
|fact store manager|The component that retrieves the fact information from the various FactRetriever objects.|  
|failover transport|A secondary transport.|  
|fallback trading partner agreement|A collection of settings that BizTalk Server uses for business-to-business message handling, when no explicit agreement is present.|  
|File adapter|An adapter that can read messages from the file system and submits them to the server. The file adapter also writes messages from the server to a file on the file system.|  
|Filter Expression property|A property of a Receive shape that determines which messages can be received. The Receive shape must have the Activate property set to True to have a filter expression.|  
|Find Message view|A reporting view that enables users to find messages based on tracked message properties.|  
|FTP adapter|An adapter that enables exchange of files between BizTalk Server and FTP servers.|  
|function|An abstraction that is used to access class members in both the action and predicate definitions. A function is used in actions and as a term in a predicate.|  
|functoid|An executable module that performs a specific calculation or data manipulation, and that is used graphically when constructing BizTalk Server maps to provide the basis for richer transformations than what is provided by XSLT on its own.|  
|Functoid IntelliSense|A BizTalk Mapper functionality in which visual cues are provided on the grid surface, when there are errors in functoid configuration.|  
|functoid toolbox|A dockable window in Visual Studio that serves as the palette of functoids available for use during map construction. Functoids are organized into different toolbox tabs based on their intended purpose.|  
  
## G  
  
|Term|Definition|  
|----------|----------------|  
|GAC|See global assembly cache.|  
|global assembly cache (GAC)|A container on a BizTalk server for a group that holds the same assemblies that are deployed to the configuration database for that group.|  
|global port|The friendly name used to associate a port with a partner profile.|  
|group header|In EDI, the part of the message used to indicate the start of a functional group of documents.|  
|group-level setting|One of the settings that BizTalk administrators can modify in the BizTalk Settings Dashboard. Examples include properties like the configuration refresh interval, maximum message batch size, and group-level tracking.|  
|group trailer|In EDI, the part of the message used to indicate the end of a functional group of documents.|  
|GS segment|In EDI, the functional group header segment of a set of ANSI X.12 documents (transaction sets) of the same document type. This required segment contains information about a group of transaction sets in the interchange, such as Application Sender Code, Application Receive Code, Group Control Number, Version/Release/Industry ID, and so on.|  
  
## H  
  
|Term|Definition|  
|----------|----------------|  
|handler|An instance of a BizTalk host on which an adapter is running.|  
|hash|A fixed-size result that is obtained by applying a one-way mathematical function (sometimes called a hash algorithm) to an arbitrary amount of data. If the input data changes, the hash changes. The hash can be used in many operations, including authentication and digital signing. Also known as message digest.|  
|health monitoring|The process of monitoring applications, components, and servers on which a BizTalk Server solution is implemented for the purposes of preempting or fixing problems.|  
|Health Monitoring cube|An online analytical processing (OLAP) cube that contain information about messages and services. Two cubes included with BizTalk Server are: Message Facts and Service Facts.|  
|hierarchical view|The left pane of the Tracking Profile Editor (TPE) and the area where the reporting namespaces and Business Activity views are created. Its main purpose is to represent the tracking profile.|  
|History database|A backend database specific to the Business Process Management scenario.|  
|host|A logical container representing one or more BizTalk Server run-time instances. This is the process space within which information about artifacts resides (that is, all the orchestrations, schemas, receive locations, and adapters that reside within a host). The host also serves as a security domain within Windows - it represents a virtual process boundary within which host instances run on one or more servers.|  
|host instance|A Windows NT Service. A host instance is the physical representation of a host on a specific server.|  
|host instance–level setting|One of the settings that BizTalk administrators can modify in the BizTalk Settings Dashboard. Examples include .NET CLR settings and properties related to an orchestration memory throttling. Specific to a given host instance, host-level settings essentially govern the use of a computer's resources (such as RAM or I/O). An example is Max. I/O Threads.|  
|host-level setting|One of the settings that BizTalk administrators can modify in the BizTalk Settings Dashboard. Examples include host tracking, and properties related to resource-based throttling, rate-based throttling, and orchestration throttling. Host-level settings tweak the way all instances of host behave in a given deployment. For example, if for Host1 the setting Max. engine threads is changed to 200, all instances of Host1 will work with a maximum of 200 engine threads.|  
|host load balancing|The process of adding multiple servers running BizTalk Server to a BizTalk group and then configuring multiple instances of an in-process host to run on these servers. This distributes the execution of services and artifacts configured in that host across multiple instances of the host, which enhances its availability and scalability.|  
|host type|A property that determines whether the host is controlled within or outside of the BizTalk Server process. Host types are In-process or Isolated.|  
|HTTP adapter|An adapter that enables exchange of messages between BizTalk Server and any application using the HTTP or HTTPS protocol.|  
  
## I  
  
|Term|Definition|  
|----------|----------------|  
|IDE|See Integrated Development Environment.|  
|Import/export|In BizTalk Settings Dashboard, to import/export settings and bindings. The current BizTalk settings for group, host, and host instance are exported and saved as an XML file. BizTalk administrators import these settings to apply them to another BizTalk environment.|  
|Import Wizard|A wizard that you start from the BizTalk Administration Console to import resources from an MSI file into a BizTalk application. If the specified application does not exist, the Import Wizard automatically creates it.|  
|independent composition|The sequencing of two actions where the second action does not depend on a sync message from the first action before the second action begins processing business logic; the second action can begin immediately.|  
|infotip|A tooltip used to provide a description for desktop, window, and Start menu commands, in Web views, and in the Windows Explorer Comment column when Details view is used.|  
|inheriting|In the Trading Partner Management (TPM) Web service, the concept that a member profile will inherit all the preferences of its parent group. In the case of a non-inheriting group, the member profile does not inherit any preferences from the parent group. A non-inheriting group can be changed to an inheriting group; however, an inheriting group cannot be changed to non-inheriting group.|  
|initerruptible orchestration|An orchestration that can be interrupted in mid-process at well-defined points.|  
|In-process host|A host type that operates within the BizTalk Server process space. Any orchestration can be enlisted to an In-process host, and any send handler can be hosted by it. In-process hosts can only host receive handlers for In-process hosts (File adapter).|  
|In-process receive adapter|An adapter that is hosted in the BizTalk Server processes. It is created, controlled, and destroyed by server processes.|  
|Installation Wizard|A wizard that you can start during the final step of the Import Wizard to install a BizTalk application on the local computer.|  
|instance activity|A series of contiguous processing steps through which one or more messages flow.|  
|instance message|A discrete unit of run-time data flowing through BizTalk Server, usually representing a particular business document such as a purchase order, and as differentiated from the BizTalk Server schema that defines its structure.|  
|Integrated Development Environment (IDE)|A combined set of Microsoft Windows-based user interface (UI) tools for building, testing, and refining a platform and its features.|  
|interceptor|A mechanism used to extract data from processing streams and persist the data to storage.|  
|interchange|In EDI, a logical combination of documents. Interchanges are destined for a single recipient. In BizTalk messaging, an interchange is a body of data that is processed by the disassembly stage of a receive pipeline or the assembly stage of a send pipeline. The interchange contains zero or more messages. In a receive pipeline, the disassembler extracts the messages contained in the interchange it received, and propagates these messages further down the receive pipeline.|  
|interchange header|In EDI, a part of an interchange, or group of logically associated documents, used to indicate the start of the interchange.|  
|interchange trailer|In EDI, a part of an interchange, or group of logically associated documents, used to indicate the end of the interchange.|  
|intergroup adapter|A BizTalk Server adapter that targets intranet/LAN communication between two BizTalk Server groups without requiring intermediate storage.|  
|internal message format|The format of the message after or before it is processed by BizTalk Server. For example, BizTalk Server receives a message, at the start of the receive pipeline, in the external format. After the message goes through the pipeline, it is in the internal format.|  
|Isolated host|A host type that operates outside of the BizTalk Server installation. An Isolated host cannot have orchestrations enlisted to it, host a send handler, use host tracking, or be used as the default host for the group. Only those receive handlers for Isolated hosts (HTTP, SOAP) can be hosted by an Isolated host.|  
|isolated receive adapter|The receive adapter that is hosted in a process other than a BizTalk Server process. This adapter is created and controlled by external process and it registers with BizTalk server at run time to submit messages.|  
  
## K  
  
|Term|Definition|  
|----------|----------------|  
|Key Performance Indicator (KPI)|Customizable business metrics provided by Analysis Services. KPIs consist of relevant attributes and associated calculations that generate industry-standard goals and benchmarks. A KPI collection includes a measure, a goal, display properties, and variances. Companies use KPIs to track performance and improve decision-making abilities.|  
  
## L  
  
|Term|Definition|  
|----------|----------------|  
|late bound port|A port defined in the orchestration, which has the Binding property set to Specify later. A late bound port is configured when it is bound to a physical port. The binding is performed using the    BizTalk Administration Console.|  
|line-of-business application|An application that is vital to running enterprises, such as payroll, resource planning, supply chain management, and accounting.|  
|live data|Data that is currently being processed by BizTalk Server.|  
|locally unique identifier (LUID)|A name for an artifact that identifies it uniquely in the BizTalk group. The elements comprising the LUID may vary, depending on the type of artifact. For example, the LUID for a BizTalk assembly includes its name, version, culture, and public key token, such as Microsoft.BizTalk.Hws.HwsPromotedProperties, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35.|  
|long-running transaction|A collection of actions treated as a unit, typically used to maintain an appropriate state in a robust and predictable fashion. The transaction can take place over an indefinite period of time and contain several nested transactions.|  
|looping record|A structure that can have more than one occurrence in an instance message.|  
  
## M  
  
|Term|Definition|  
|----------|----------------|  
|Management database|A Microsoft SQL Server database that stores the configuration information for resources in an organization. There is one Management database (sometimes referred to as the configuration database) per organization.|  
|map|An XML file that defines the correspondence between the records and fields in one specification and the records and fields in another specification. A map contains an Extensible Stylesheet Language (XSL) stylesheet that is used by BizTalk Server to perform the transformation described in the map.|  
|mapper grid|The multi-layered middle area of the main BizTalk Mapper window, between the source and destination schemas, in which data mapping is defined.|  
|mapper grid page|A single layer in the mapper grid, used to organize related data mappings separate from other data mappings.|  
|master secret|A key generated by the master secret server when an Enterprise Single Sign-On (SSO) Administrator requests it. This secret key is stored in the registry as a Local Security Authority (LSA) secret on the master secret server. Only SSO Administrators can access this secret key.|  
|master secret server|In a distributed Enterprise Single Sign-On (SSO) environment, the one computer that holds the master secret key in the registry. There can be many SSO servers (on different machines) accessing this single SSO database. Only one of these SSO servers is designated to be the master secret server.|  
|message|An electronic instance of data, as typically exchanged between two running business processes or applications.|  
|message body part|The main part of a BizTalk Server message, which contains the actual payload, and in most cases an XML blob. All messages must have at most one body part. Typically the data read from the stream corresponding to the BizTalk Server message body part is used for promoting message context properties. Hence the routing, publication, or subscription that is based on promoted properties is generally done based on the body part.|  
|message context|A container for various properties that are used by BizTalk Server when processing a document.|  
|message context properties|A set of properties associated with the message.|  
|Message Details view|On the Group Hub page, a detailed view of all known information for a given message in the MessageBox. This view is available through the shortcut menu in the PivotTable field list in one of two Operations views.|  
|message digest|See Other Term: hash|  
|Message Facts cube|An online analytical processing (OLAP) cube that aggregates information about messages and services. Two cubes included out of the box are: Message Facts and Service Facts.|  
|message flow|A series of contiguous processing steps through which one or more messages flow.|  
|Message Flow view|A view on the Group Hub page that displays a history of processing events for specific messages.|  
|message header|In EDI, a part of the message used to indicate the start of a document, which is a bundle of logically combined segments containing information about one transaction. In ANSI X.12, a message is equivalent to a transaction set.|  
|message instance|An instance of a message that BizTalk Server is either processing or has serialized into the MessageBox or Tracking datastore for further processing or tracking, respectively. Within BizTalk Server, this is usually a reference to the message, the promoted properties of the message, and the message body.|  
|Message Metrics view|The PivotTableview into a message metrics online analytical processing (OLAP) cube.|  
|message trailer|In EDI, a part of the message used to indicate the end of a document, which is a bundle of logically combined segments containing information about one transaction. In ANSI X.12, a message is equivalent to a transaction set.|  
|MessageBox binding|A binding that interacts with the MessageBox.|  
|MessageBox database|A group of Microsoft SQL Server databases that contain subscription and tracking information for a MessageBox group.|  
|MessageBox node|In the BizTalk Administration console, the node used to view a list of the currently running MessageBox databases.|  
|Messages view|On the Group Hub page, a live view of message instances used by services in a MessageBox. The view is available in the Operations menu.|  
|Messaging|One of the primary functions of BizTalk Server, involving the reliable reception, routing and distribution of messages.|  
|Messaging Instance|On the Group Hub page, messaging instances include send port and receive port service instances. Messaging instances refer to messaging service instances.|  
|Metadata|Information, such as location, time, message size, and/or exception information.|  
|milestone alias|In BAM, the name by which you refer to a milestone or data item contained by BAM activities. Each milestone and data item can have multiple aliases.|  
|mixed content|The content of a particular XML element that contains both subelements and data that is not within the subelements. An example from HTML is: &lt;P&gt;Full moons &lt;EM&gt;always&lt;/EM&gt; rise at sunset, more or less.&lt;/P&gt;|  
|multi-part message type|A definition of the structure of a message, including the data types of its elements. A multi-part message type can contain a single part or many parts.|  
  
## N  
  
|Term|Definition|  
|----------|----------------|  
|native|Any data format other than XML.|  
|native adapter|The adapters supplied by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], which includes MQSeries, File, FTP, HTTP, SMTP, SOAP, and SQL adapters.|  
|native pipeline component|A pipeline component that is provided by Microsoft and ships with BizTalk Server.  Examples of this are the Flat File disassembler, the XML disassembler, and  the S/MIME Decoder.|  
|node|The entry in a schema tree displayed within BizTalk Editor and BizTalk Mapper.|  
  
## O  
  
|Term|Definition|  
|----------|----------------|  
|OLAP|See online analytical processing.|  
|online analytical processing (OLAP)|A technology that uses multidimensional structures to provide rapid access to data for analysis. The source data for OLAP is commonly stored in data warehouses in a relational database.|  
|operation|A request or request-response pairing on a port that is associated with either a send or receive action.|  
|Operations views|On the Group Hub page, views that enable the user to view but not track live data.|  
|Operations/Message Details view|A detailed view of all known information for a given message in the MessageBox.|  
|Operations/Messages view|A live view of messages used by services in the MessageBox database.|  
|Operations/Service Instance Details view|A detailed view of all known information for a given service instance in the MessageBox.|  
|Operations/Service Instances view|A live view of services (active or suspended) in the MessageBox database; in BizTalk Server 2002, the WorkQ/SuspendedQ.|  
|orchestration|An executable business process.|  
|orchestration binding|An orchestration port that does not connect to a fixed endpoint, but instead connects to the MessageBox directly.|  
|Orchestration Designer|A graphical user interface tool used to design and implement business processes.|  
|orchestration instance|A running instance of a specific executable business process.|  
  
## P  
  
|Term|Definition|  
|----------|----------------|  
|PAM|See Partner Agreement Management (PAM).|  
|parameter|Refers to the default parameters of a business process, parameters for a business process per partner, and parameters for a business process per partner group.|  
|partner|See Other Term: trading partner|  
|Partner Agreement Management (PAM)|A user interface in the Parties node of the BizTalk Server Administration Console where you set party properties. You can set processing properties for parties engaging in EDI document exchange, EDI batching, AS2 document transport, and global properties to be used in the absence of a party.|  
|party|Each entity outside of BizTalk Server that interacts with an orchestration. All of the partners your organization deals with are considered parties, and your organization may have several has several thousands partners.|  
|party enlistment|The mechanism that ties a party to a role. You can enlist a party in a role, and that enables the orchestration to interact with the party|  
|pass-through|A configuration of BizTalk Server ports such that a receive port is directly connected to a send port by using only one filter expression on a send port. The filter expression should take the form BTS.ReceivePortName == "Name or receive port". In this configuration, any message that is received by the receive port is directly routed to a send port. The meaning of pass-through execution in BizTalk 2004 is different from the meaning of pass-through execution in BizTalk Server 2000 or 2002. In BizTalk Server 2004, the pass-through execution message is still processed in pipelines and may be transformed in ports as well.|  
|performance monitoring|The process of watching the message process/receive rate, number of running orchestrations, number of cache hits, memory usage over time, and so on.|  
|performance processing rules|Rules that govern process performance or capacity type counters.|  
|perimeter network|A collection of devices and subnets placed between an intranet and the Internet to help protect the intranet from unauthorized Internet users. Also known as DMZ, demilitarized zone, and screened subnet.|  
|physical (early) binding|Information that is carried in the assembly and used by the deployment process to create send and receive ports.|  
|pipeline|A software infrastructure that defines and links one or more processing stages, running them in prescribed order to complete a specific task. Pipelines divide processing into stages, abstractions that describe a category of work. They also determine the sequence in which each category of work is performed.|  
|pipeline component|A COM or .NET-based component that can be placed into a pipeline to perform some processing action on the messages going through that pipeline.|  
|Pipeline Designer|A graphical user-interface tool used to create and configure pipelines in BizTalk Server.|  
|policy|A versioned collection of business rules.|  
|port connector line|A line showing the connection between a Send/Receive shape and an operation on a Port shape. Neither endpoint of a port connector line can remain unattached.|  
|port type|A property that defines the set of message interaction patterns called operations that are permitted at that endpoint. An operation can be one-way, in which case one message is sent or received, or it could be request-response in which case a message is sent (or received) and a response is received (or sent).|  
|positional flat file|A type of file format used to represent business documents in which the records and fields have a fixed length, eliminating the need for delimiters.|  
|private queue|A queue that is not published as an Active Directory object. BizTalk message queuing fully supports the sending and receiving of messages into private queues.|  
|process surface|The middle area of the design surface in the Orchestration Designer. This area is used to design orchestrations.|  
|Project Designer|A visual representation of the services, ports, and bindings that make up a project. Users can edit the visual items in the Project Designer by adding and removing services, and creating and removing bindings between compatible ports on the services in the designer.|  
|property promotion|The mechanism through which specific message properties are written to the message context associated with the message as property fields. Properties written to the message context as property fields are considered to be promoted properties (the **IsPromoted** property of the field is set to **True**) and require an associated property schema.  Property fields are used by the BizTalk Server Messaging Engine for purposes of document routing, message tracking, and for evaluation in orchestrations. The message context for a message is stored in the imgContext column of the row for the message in the spool table of the MessageBox database.|  
|property schema|A schema that you associate with a BizTalk Server schema, and used to identify the element fields in a document that will be promoted to the message context as property fields.|  
|protocol setting|A setting that defines how business transactions are to be supported for a specific business-to-business protocol. Each business profile defines the various settings for processing messages (encoding) or transmitting messages (transport) for each of the business-to-business protocols over which the partner can communicate. A protocol setting can be for encoding protocols or for a transport protocol.|  
|public queue|A queue that is published as an Active Directory object.|  
|publication-subscription|See Other Term: publish/subscribe architecture|  
|publish/subscribe architecture|The combination of publication and subscription used  to move messages between subsystems. For example, receive ports receive messages, process them and  publish them to the MessageBox. BizTalk Server routes these messages to subscribing orchestrations or send ports that further process the documents and either republish them to the MessageBox or send them to external systems.|  
|publishing|The act of storing a message instance in the MessageBox database so that it can be matched to a subscription from a consuming application.|  
  
## Q  
  
|Term|Definition|  
|----------|----------------|  
|Query Expression|A group of query clauses on the Group Hub page that you can use to create and run queries against the BizTalk Tracking database.|  
  
## R  
  
|Term|Definition|  
|----------|----------------|  
|range dimension|In BAM, a dimension used to create ranges of crirteria. For example, you could create Low (0-100), Medium (100-500), and High (500-1000) ranges to describe sales of numerical units.|  
|receipt generator|A component that generates a fake receipt to remove a message from the Retry Queue.  This component is used if a messaging port is configured to use Reliable Messaging.|  
|receive handler|An instance of a BizTalk host on which a receive adapter is running. A receive handler is a logical container for a Listener component, an Endpoint Manager component, and a MessageAgent component.|  
|receive handler host type|A property that restricts the host type by which a particular receive handler can be hosted.|  
|receive location|The physical, design-time notion of a location (such as a URL) and an adapter type. A receive location in the Host node in the BizTalk Server Administration console defines the receive functionality.|  
|receive pipeline|A pipeline that is executed on messages after they have been received by an adapter and before they are published into the MessageBox database.|  
|receive port|A logical grouping of similar receive locations.|  
|redeploy|The act of redeploying an assembly that already exists in the target environment by deleting the old bits and deploying the new ones.|  
|rehydrate|To activate an idle orchestration in memory from persistent storage as a result of some event taking place, such as a message being received.|  
|Relevance view|A view in BizTalk Mapper whereby non-relevant siblings of a schema element collapse to provide a more compact view of the schema. This reduces the need for scrolling, and brings the focus to the useful parts of the schema and map.|  
|Reporting vews|A hierarchical set of views that show a business process or processes.|  
|repository|The storage container for the metadata used by Analysis Services. Metadata is stored in tables in a relational database and is used to define the parameters and properties of Analysis server objects. XML tools use the repository in read-write mode, while BizTalk Explorer accesses the data in read-only mode.|  
|request-response adapter|A receive adapter that receives a request message from the client, submits it to the server, waits for a response, and then sends the response back to the client.|  
|Return shape|A shape used to terminate an orchestration at some point before the orchestration's true end.  An example of this might be: If (security check passed) continue, else Return.|  
|role|A collection of port types that either uses a service or implements a service, providing the means by which parties interact with orchestration(s). For example, an orchestration might use the role of a Shipper. The Shipper would have one or two parties associated with it. When the orchestration decides which shipping company to use to ship an item, it compares the prices of the parties in the Shipper role.|  
|role link|The relationship between roles by defined by the message and port types used in the interactions in both directions.|  
|role link type|A property that characterizes the relationship between two services or orchestrations by defining the part played by each of the services in the relationship and specifying the port types provided by each role.|  
|root node|A node within a BizTalk Server schema that represents the outermost XML element in the business document specified by the schema.|  
|RTA window|Defines the time period over which the data in a real-time aggregation (RTA) is aggregated. For example, if the time period is one day and the point in time is now, then you see aggregations only on the data from the last 24 hours. As the point in time is continuously changing, the time period in the RTA window is also changing; therefore, it is also referred to as a moving time window.|  
|rule|A pairing of conditions and actions.|  
|rule set|A logical grouping of similar rules. This can be viewed as a grouping/partitioning mechanism of the rule engine.|  
|Rules Engine Framework|The .NET component library, APIs, and services used by application developers to write rule-based applications.|  
|Rules Engine Update service|A service that performs dynamic policy updates.|  
|Rules store|A location for persisting policies. A SQL Server database is the default rule store.|  
  
## S  
  
|Term|Definition|  
|----------|----------------|  
|schema|The structure for a message. A schema can contain multiple sub-schema.|  
|Schema Editor extension|The mechanism through which software modules extend the basic XML/XSD functionality supported by BizTalk Editor. Schema Editor Extensions typically add supplemental properties to one or more nodes in BizTalk schemas to represent their particular semantics.|  
|screened subnet|See Other Term: perimeter network|  
|Secure Sockets Layer|A protocol that improves the security of data communication by using a combination of data encryption, digital certificates, and public key cryptography. SSL enables authentication and increases data integrity and privacy over networks. SSL does not provide authorization or nonrepudiation.|  
|segment|In EDI, a logical combination of elements. For example, name and address details are combined in one segment.|  
|segment tag|In EDI, a unique identifier for a segment. Within EDIFACT, for example, segment tags are three-letter uppercase codes that prefix the elements within a document. In ANSI X.12, the segment tags are two or three-letter uppercase codes. A segment tag is similar to a record type identifier.|  
|send handler|A BizTalk host with which the send adapter is associated.|  
|send pipeline|A pipeline that is executed on messages before they are sent out of the BizTalk server.|  
|send port|The location to which messages are sent or from which messages are received, and the technology that is used to implement the communication action. The location is uniquely identified by the name of the port.|  
|send port group|A logical grouping of send ports. When a message is sent to a send port group, it is routed to all of the associated send ports. Also referred to as a distribution list.|  
|service|A program, routine, or process that performs a specific system function to support other programs at the operating systems level, such as a Windows NT service. A service is a Windows NT service or a COM+ service that runs on a server.|  
|service instance|Generally refers to an instance of an orchestration that BizTalk Server is either processing or has serialized into the MessageBox for further processing or tracking. This is usually a serialized representation of the state of the orchestration and references to any messages in use within the orchestration. In the context of messaging, a service instance applies to an instance of a port, for example, a receive port where the input is the receive location and the output is publishing to the MessageBox database, or a send port where the input is the MessageBox and the output is typically a send adapter.|  
|Service Metrics view|A PivotTable view into the service metrics OLAP cube. Formerly part of Aggregation view.|  
|session|A logical connection created between two hosts to exchange data. Typically, sessions use sequencing and acknowledgments to send data.|  
|shape|A graphical representation of an action or grouping of actions in an orchestration.|  
|shape connector line|A line used to link shapes and determine their relative order in an orchestration.|  
|Simple shape|A shape in an orchestration that cannot be collapsed and cannot contain other shapes.|  
|Single Sign-On|See Other Term: Enterprise Single Sign-On system|  
|Single Sign-On administration|The object model accessed by administrative command line utilities (such as ssomanage and ssoconfig), and by Windows Management Instrumentation (WMI) and BizTalk Explorer for configuration store scenarios. This component communicates with the SSO database using the SSO Server.|  
|Single Sign-On Administrators group|The Administrator who has the highest level of authority and typically sets up the encryption key.|  
|Single Sign-On Affiliate Application Administrators group|Administrators who can create and manage affiliate applications, specify the Single Sign-On Application Administrators account for each affiliate application, and perform all the administration tasks that the Single Sign-On Application Administrators and Single Sign-On application users can do.|  
|Single Sign-On Application Administrators group|Administrators who are assigned specifically to each affiliate application.|  
|Single Sign-On client utilities|Available as part of the Administration feature, utilities for end-users to provide their credential mappings in the SSO database. These are used by the SSO server to communicate with the SSO database.|  
|Single Sign-On (SSO) database|The database in which Enterprise Single Sign-On (SSO) credentials are stored. Other databases store the URLs and send ports; only one has the secret sub-service.|  
|Single Sign-On server|The server on which the Enterprise Single Sign-On (SSO) service is installed.|  
|Single Sign-On services|Services that enable single sign-on for adapters by accessing credentials in the SSO database. These services are used to manage and administer the SSO database. As a configuration store, these services are used to access configuration data for adapters.|  
|Smart Tag|A graphical warning that a shape is not fully configured, and which provides hints on how to proceed.|  
|SMTP adapter|An adapter that implements the SMTP protocol (that is, sends e-mail messages) to interact with line-of-business applications. This adapter includes only the send handler.|  
|SOAP adapter|An adapter that implements the SOAP protocol to interact with line-of-business applications, publishes orchestrations as Web services, and consumes external Web services.|  
|SOAP fault|An error message returned by a Web service that conveys an application exception in the Web service.|  
|SOAP header|An optional element contained within the envelope of a SOAP message that can contain data not dirrectly related to the XML Web service method's primary functionality.|  
|SOAP message|A well-formed XML document. It should use the SOAP envelope and SOAP encoding namespaces and include an optional XML declaration, followed by a SOAP envelope (the root element), which is made up of an optional SOAP header and a SOAP message body.|  
|SOAP message tracing|A method for setting a breakpoint in a published Web service to return detailed exceptions to a Web client.|  
|solicit-response adapter|A two-way send adapter. A solicit-response send adapter sends a request message from BizTalk Server to a destination, waits for a response message, and then submits the response message back to BizTalk Server.|  
|source schema|The schema used in a BizTalk Server map that represents the structure of the output instance messages.|  
|SQL adapter|An adapter that exchanges information between BizTalk Server and a SQL Server database.|  
|SSO|See Enterprise Single Sign-On system.|  
|stage|A portion of a pipeline dedicated to completing a certain category of work. The pipeline components within the stage complete the actual tasks.|  
|staging database|A database used by a tester to deploy the assembly with its bindings to the test or staging database.|  
|static adapter|An adapter that uses the user interface provided by the adapter framework.|  
|static port|A send port that has a destination address and adapter type associated with it. As opposed to a dynamic send port, a static send port cannot change its configuration at run time and is always used to send messages to only one destination address.|  
|strong name key file|A file that contains the identity for an assembly - its simple text name, version number, and culture information (if provided) - plus a public key and a digital signature. It is generated from an assembly file using the corresponding private key. (The assembly file contains the assembly manifest, which contains the names and hashes of all the files that make up the assembly.)|  
|submit|The act of placing a message and associated properties in the appropriate tables in the MessageBox database and scanning the Subscription directory for subscriptions whose predicates match the properties of the message.|  
|subscribe|A BizTalk mechanism for instructing the MessageBox to route messages with properties that meet specified parameters (subscriptions) to the appropriate processes. For example, send port filters create subscriptions in the MessageBox. When messages are published to the MessageBox that match the filter specification, BizTalk Server routes the messages to the subscribing send port for processing.|  
|subscription|A mechanism to route messages that match certain property comparison criteria into a Work queue.|  
|Subscription database|The MessageBox database that contains all of the subscriptions for a MessageBox group.|  
|suspended instance|An instance of a message or orchestration that BizTalk Server has stopped processing, due to an error in the system or the message. Generally, suspended instances caused by system errors are resumable upon resolution of the system issue. Often, suspended instances due to a message problem are not resumable, and the message itself must be fixed and resubmitted to the BizTalk Server system.|  
|Suspended queue|A queue that contains work items for which an error or failure was encountered during processing. A suspended queue stores the messages until they can be corrected and reprocessed, or deleted.|  
  
## T  
  
|Term|Definition|  
|----------|----------------|  
|target database/environment|Identified when deploying an assembly and its bindings into a target environment.|  
|task|The human touch point within an action. Each action can have zero or more tasks that are each assigned to different targets. There is a one-to-one correspondence between tasks and targets.|  
|task response|The responses to the task from the targets. Each task can have zero or more responses.|  
|TDDS|See Tracking Data Decode Service.|  
|Technical Details view|A view on the Group Hub page that displays the technical processing steps along a single thread of activity.|  
|term|The atomic entity with a value that can be used in predicates and actions. Can be a class member (.NET class property, method, or field, XML element, database element), rule variable, or a constant.|  
|time dimension|A UI element that describes time as it is used in aggregations.|  
|timer message|A timer message inserted in the message queue that triggers moving the stream back to the queue.|  
|toolbox|A dockable window containing a variety of elements that can be used in the orchestration design process.|  
|tooltip|A little pop-up window that provides brief context-sensitive help when you move the mouse pointer over the item.|  
|TPE|See Tracking Profile Editor.|  
|tracking|The ability to track interchanges and messages processed by BizTalk Server.|  
|Tracking Analysis database|The name of the tracking analysis (OLAP) database for the associated MessageBox group.|  
|Tracking Data Decode Service (TDDS)|A service that moves event data from the MessageBox database to the BAM Primary Import database. This service processes and persists both Business intelligence and BizTalk Health Monitoring data.|  
|Tracking database|A Microsoft SQL Server database that stores the tracking information for a MessageBox group. There is one Tracking database per MessageBox group.|  
|Tracking Options view|A view on the Group Hub page that defines the tracking options.|  
|tracking profile|A set of characteristics that define a business-related process and contains the mapping between a specific orchestration and activity definition.  A tracking profile is a file with a .btt extension.|  
|Tracking Profile Editor|A graphical user-interface tool used to define the interesting parts of their business process as well as interesting business payload data.|  
|trading partner|An external or internal organization with which your organization exchanges electronic data. For example, a trading partner could be a supplier, a customer, or an internal department.|  
|trading partner agreement|A definitive and binding agreement between two trading partners for transacting messages over a specific business-to-business protocol. A trading partner agreement brings together common bi-directional message processing properties from specific business profiles of both partners. It is a comprehensive collection of all aspects governing the business transaction between the two trading partners. The trading partner agreement is typically derived from the profiles of each partner, with the ability to customize and override the required settings.|  
|trading partner management|The act of managing and storing information about partners, their business, and business-to-business relationships/agreements. The enhanced trading partner management (TPM) solution more intuitively reflects the business entities and relationships, thereby enabling organizations to better manage business partnerships with trading partners.|  
|trading party|An entity that is at the root level of a trading partner management (TPM) solution. Each participating organization in an ongoing business relationship, and any single business entity that is running BizTalk Server and sending or receiving messages to or from any other party, is a trading party.|  
|transactional messaging|A stream of messages sent in order exactly once, achieved by synchronizing and coordinating multiple BizTalk message queuing adapter instances in a group.|  
|Transform shape|A shape in an orchestration that is used to move data from one message into another message, and have it transformed using an XSLT map.|  
|transformation|The process of converting an XML document that conforms to one schema into an XML document that conforms to another schema, often changing the document structure in the process.|  
|translation|The process of converting an XML document into native (non-XML) format, or vice versa.|  
|transport agreement|An agreement between the business profiles of two trading partners to use a specific transport protocol (AS2) while exchanging messages.|  
|Transport Layer Security|A protocol that provides communications privacy and security between two applications communicating over a network. TLS encrypts communications and enables clients to authenticate servers and, optionally, servers to authenticate clients. TLS is a more secure version of the Secure Sockets Layer (SSL) protocol.|  
|transport protocol|A protocol that governs the transport channel used for sending messages back and forth between two partners. With respect to trading partner management (TPM), only the AS2 protocol is supported.|  
  
## U  
  
|Term|Definition|  
|----------|----------------|  
|undeploy|The process of deleting a BizTalk application from the BizTalk Server databases and Administration Console, as well as removing the application from any computers on which it was installed.|  
|unenlist|The act of eliminating all subscriptions and instances (running or suspended) for that service.|  
|United Nations Trade Data Elements Dictionary (UNTDED)|In EDI, the dictionary of all elements used within the EDIFACT standard.|  
|UNTDED|See United Nations Trade Data Elements Dictionary.|  
|UNZ segment|In EDI, the Interchange Trailer segment of an EDIFACT document. It includes the elements Interchange Reference and Number of Documents in the interchange. The segment is used to indicate the end of an interchange and to check the interchange reference and number of documents in the interchange.|  
  
## V  
  
|Term|Definition|  
|----------|----------------|  
|versioning|The act of updating the implementation of an artifact and incrementing its version number.|  
|virtual node|In schema, a node that does not correspond directly to an XML element or attribute in the instance messages defined by the schema.|  
|vocabulary|A collection of vocabulary elements used in rule composition.|  
|vocabulary element|A human-readable name for facts.|  
  
## W  
  
|Term|Definition|  
|----------|----------------|  
|Web services|A unit of application logic providing data and services to other applications. Applications access XML Web services using standard Web protocols and data formats such as HTTP, XML, and SOAP, independent of how each XML Web service is implemented. XML Web services combine the best aspects of component-based development and the Web, and are a cornerstone of the Microsoft .NET programming model.|  
|Web Services Description Language (WSDL)|An XML-formatted language that describes Web services as endpoints for exchanging messages. It is extensible to allow for the description of endpoints and their messages regardless of the message format and network protocol. It is the language used by Universal Description, Discovery, and Integration (UDDI), which is a Web-based business directory.|  
|Windows Management Instrumentation (WMI)|A component of the Microsoft Windows operating system and the Microsoft implementation of Web-Based Enterprise Management (WBEM), used to automate administrative tasks in an enterprise environment.|  
|WMI|See Windows Management Instrumentation.|  
|work queue|A queue that contains messages to be processed by a BizTalk server.|  
|WSDL|See Web Services Description Language.|  
  
## X  
  
|Term|Definition|  
|----------|----------------|  
|X.509 certificate|The standard certificate format used by Windows certificate-based processes. An X.509 certificate includes the public key and information about the person or entity to whom the certificate is issued, information about the certificate, plus optional information about the certification authority (CA) issuing the certificate.|  
|XDR|See XML-Data Reduced.|  
|XML Schema definition language (XSD)|A schema language. An XML Schema defines the elements, attributes, and data types that conform to the World Wide Web Consortium (W3C) XML Schema Part 1: Structures Recommendation for the XML Schema Definition Language. The W3C XML Schema Part 2: Datatypes Recommendation is the recommendation for defining data types used in XML schemas. The XML Schema definition language enables you to define the structure and data types for XML messages.|  
|XML-Data Reduced (XDR)|One of several ways in which the structure of an XML document can be described.  BizTalk Server can open a schema described using XDR, but converts it to XML Schema definition language (XSD) in the process.|  
|XPath|A comprehensive language used for navigating through the hierarchy of an XML document. XPath expressions can contain XML element and attribute information, select data that matches specific criteria, and perform comparisons on the data retrieved. Also called a node path.|  
|XSD|See XML Schema Definition language.|  
|XSLT|See Extensible Stylesheet Language Transformations.|  
  
## Z  
  
|Term|Definition|  
|----------|----------------|  
|zombie|A message that was not processed by an orchestration. It is not in the Suspended queue or anywhere else where it will be retried.|  
|zombie resurrector|An orchestration that listens at the MessageBox database for zombies and resurrects those that meet certain criteria.|