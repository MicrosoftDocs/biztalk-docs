---
title: "Glossary | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2de64458-169e-4051-8b4b-5aa6cab5d0f4
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Glossary
**3270**  
 The information display system for IBM hosts (mainframes). The system includes terminals, printers, and controllers that enable a user to access host functions.  
  
 **5250**  
 The information display system for IBM AS/400 computers.  
  
 **802.2**  
 The logical link control protocol used for communication over a Token Ring or Ethernet network. The 802.2 protocol is an IEEE standard.  
  
 **1-byte unsigned Integer**  
 An integer data type that has a positive value ranging from 0 to 255.  
  
 **2-byte signed Integer**  
 An automation integer data type that can be either positive or negative. The most significant bit is the sign bit, which is 1 for negative values and 0 for positive values. The storage size of the integer is 2 bytes. A 2-byte signed integer can have a range from -32,768 to 32,767.  
  
 **2PC**  
 *See* **two-phase commit (2PC)**.  
  
 **4-byte Real**  
 Also referred to as a single-precision floating-point or Single. Single variables are stored as IEEE 32-bit (4-byte) floating-point numbers, ranging in value from –3.402823E38 to –1.401298E-45 for negative values and from 1.401298E-45 to 3.402823E38 for positive values. The type-declaration character for Single is an exclamation point (!).  
  
 **4-byte signed Integer**  
 An Automation integer data type that can be either positive or negative. The most significant bit is the sign bit, which is 1 for negative values and 0 for positive values. The storage size of the integer is 4 bytes. A 4-byte signed integer can have a range from -2,147,483,648 to 2,147,483,647.  
  
 **8-byte Real**  
 Also referred to as a double-precision floating-point or Double. Double data type variables are stored as 64-bit (8-byte) numbers. A Double variable is stored as a 64-bit (8-byte) number ranging in value from 1.79769313486232E308 to –4.94065645841247E-45 for negative values, from 4.94065645841247E-324 to 1.79769313486232E308 for positive values, and 0. The type-declaration character is a number sign (#).  
  
 **3270 emulator**  
 Software that enables a microcomputer to act as a 3270 terminal, displaying information from a host system (mainframe). Emulator software can also enable a desktop computer to send print jobs from a host system to a printer connected to the microcomputer.  
  
 **3270 terminal emulation**  
 The use of software that enables a microcomputer to act as a 3270 terminal, displaying information from a host system (mainframe). Emulation software can also enable a microcomputer to send print jobs from a host system to a printer connected to the microcomputer.  
  
 **5250 emulator**  
 Software that enables a microcomputer to act as a 5250 terminal interacting with an AS/400 system.  
  
 **5250 terminal emulation**  
 The use of software that enables a microcomputer to act as a 5250 terminal interacting with an AS/400 system.  
  
## -A-  
 **A3270**  
 The server transaction program for the APPC 3270 Terminal Emulator facility.  
  
 **abend**  
 Short for abnormal end. The premature ending of a program because of program error or system failure.  
  
 **ACID**  
 *See* **atomic, consistent, isolated, and durable (ACID)**.  
  
 **acknowledgment required (ACKRQD)**  
  
 A field in the header of a Status-Control message. If a Status-Control request has ACKRQD set in the message header, the recipient must supply a Status-Control response before the sender sends further messages or further Status-Control requests.  
  
 **ACKRQD**  
  
 *See* **acknowledgment required (ACKRQD)**.  
  
 **ActiveX**®  **Data Objects (ADO)**  
 A data access interface that communicates with OLE DB-compliant data sources to connect to, retrieve, manipulate, and update data.  
  
 **ACTLU**  
 SNA command sent by the system services control point (SSCP) to a logical unit (LU) to activate a session and establish session parameters.  
  
 **ACTPU**  
 SNA command sent by the system services control point (SSCP) to activate a physical unit (PU), so that any logical units (LUs) controlled by this PU are available to the SNA network.  
  
 **adapter**  
 Refers to a circuit board, network card, and similar expansion devices with a specialized function, such as controlling a video display monitor or accessing a communications line. Not the same as a driver.  
  
 **administration access**  
 The level of access available to a user. The user may be granted or denied the right to use the interfaces (Host Integration Server Setup, SNA Manager, or the **snacfg** command) to read and change the configuration file, to start and stop services and connections, or to reset LUs.  
  
 **ADO**  
 *See* **ActiveX**® **Data Objects (ADO)**.  
  
 **Advanced Peer-To-Peer Networking (APPN)**  
 An extension to SNA that features (a) greater distributed network control that avoids critical hierarchical dependencies, thereby isolating the effects of single points of failure; (b) dynamic exchange of network topology information to foster ease of connection, reconfiguration, and adaptive route selection; (c) dynamic definition of network resources; and (d) automated resource registration and directory lookup. APPN extends the LU 6.2 peer orientation for end-user services to network control and supports multiple LU types, including LU 2, LU 3, and LU 6.2.  
  
 **Advanced Program-to-Program Communications (APPC)**  
 A means of enabling programs to communicate directly with each other, across a network or within a single system. APPC uses a type of logical unit called LU 6.2, and enables transaction programs (TPs) to engage in peer-to-peer communications in an SNA environment.  
  
 (1) The general term that characterizes the LU 6.2 architecture and its various implementations in products. (2) Refers to the LU 6.2 architecture and its product implementations as a whole or to an LU 6.2 product feature in particular, such as an APPC application programming interface. (3) A method for enabling programs to communicate directly with each other across a network or within a single system. APPC uses a type of LU called LU 6.2, and enables TPs to engage in peer-to-peer communications in an SNA environment.  
  
 **AFTP**  
 *See* **APPC File Transfer Protocol (AFTP)**.  
  
 **AFTPD**  
 The server transaction program for the APPC File Transfer Protocol facility.  
  
 **aggregation**  
 A composition technique for implementing component objects whereby a new object can be built using one or more existing objects that support some or all of the required interfaces of the new object.  
  
 **alert**  
 A message that indicates an abnormal event or a failure.  
  
 **allocate**  
 (1) The process that an operating system uses to respond to a request from a program to reserve memory for use by the program. (2) In Advanced Program-to-Program Communications (APPC), a verb that assigns a session to a conversation. *Contrast with***deallocate**.  
  
 **American Standard Code for Information Interchange (ASCII)**  
 A coding scheme that assigns numeric values to letters, numbers, punctuation marks, and certain other characters.  
  
 **API**  
 *See* **application programming interface (API)**.  
  
 **APING**  
 (1) The APPC Connectivity Tester facility. (2) The client transaction program for the APPC Connectivity Tester facility.  
  
 **APINGD**  
 The server transaction program for the APPC Connectivity Tester facility.  
  
 **APPC**  
 *See* **Advanced Program-to-Program Communications (APPC)**.  
  
 **APPC File Transfer Protocol (AFTP)**  
 (1) The client transaction program for the APPC File Transfer Protocol facility. (2) An interactive full-screen environment with a specific set of commands used to manage and transfer files between a client and server computer. (3) An API that provides APPC file transfer capabilities.  
  
 **APPC mode**  
 A collection of session properties used by LU 6.2-type logical units (LUs) as they carry on a session. A mode can be used by many LU pairs at the same time.  
  
 **APPC mode name**  
 The name used to represent a set of characteristics to be used in an APPC LU-LU session.  
  
 **APPC verb**  
 The mechanism by which a program accesses APPC. Each verb supplies parameters to APPC. *See also***Advanced Program-to-Program Communications (APPC)**.  
  
 **application programming interface (API)**  
 The set of programming language constructs or statements that can be coded in an application program to invoke the specific functions and services provided by an underlying operating system or service program.  
  
 **application requester (AR)**  
 (1) The source of a request to a remote relational database management system (DBMS). (2) The Microsoft Network Client for DB2 that supports the Microsoft OLE DB Provider for DB2, Microsoft .NET Framework Data Provider for DB2, Entity Provider for DB2, and BizTalk Adapter for DB2.  
  
 **application TP**  
 An application program that uses Advanced Program-to-Program Communications (APPC) to accomplish tasks for end-users and exchange data with other transaction programs (TPs) in an SNA environment.  
  
 **APPN**  
 *See* **Advanced Peer-To-Peer Networking (APPN)**.  
  
 **AR**  
 *See* **application requester (AR)**.  
  
 **array**  
 A set of sequentially indexed elements which have the same intrinsic data type. Each element of an array has a unique identifying index number. A changes made to one element of an array does not affect the other elements.  
  
 **ASCII**  
 *See* **American Standard Code for Information Interchange (ASCII)**.  
  
 **assembly**  
 A collection of functionality built, versioned, and deployed as a single implementation unit (one or multiple files). An assembly is the primary building block of a .NET Framework application. All managed types and resources are marked either as accessible only within their implementation unit or as exported for use by code outside that unit. In the common language runtime, the assembly establishes the name scope for resolving requests and the visibility boundaries are enforced. The runtime can determine and locate the assembly for any running object because every type is loaded in the context of an assembly.  
  
 **assembly cache**  
 A machine-wide code cache used for side-by-side storage of assemblies. There are two parts to the cache. First, the global assembly cache contains assemblies that are explicitly installed to be shared among many applications on the computer. Second, the download cache stores code downloaded from Internet or intranet sites, isolated to the application that triggered the download so that code downloaded on behalf of one application or page does not impact other applications. *See also***global assembly cache (GAC)**.  
  
 **asynchronous verb completion**  
 Processing of an SNA verb where the initial API call returns immediately, so that the normal operation of the program is not blocked while processing completes. When the verb completes, the application is notified through a Microsoft® Windows® message or event. *Contrast with***synchronous verb completion**.  
  
 **atomic, consistent, isolated, and durable (ACID)**  
 An acronym that describes the four key properties required of any Windows-based transaction:  
  
-   **Atomic.** Each transaction must execute completely or not at all.  
  
-   **Consistent.** The structural integrity of the transaction database must be maintained.  
  
-   **Isolated.** A transaction cannot access data that is already involved in a transaction.  
  
-   **Durable.** The TP data must be stored securely to enable recovery of the transaction results.  
  
> [!NOTE]
>  A mainframe-based transaction program (TP) differs from a Windows-based transaction. A mainframe-based TP is a COBOL program that exists in the CICS or IMS environment and contains one or more mainframe transactions. A mainframe transaction might or might not meet the ACID properties.  
  
 **atomicity**  
 A feature of a transaction that indicates that either all actions of the transaction happen or none happens.  
  
 **auditing**  
 Tracking the activities of administrators and users by recording selected types of events (for example, the changing of the configuration file) in the security log of a computer running Host Integration Server.  
  
 **authentication**  
 The process of determining the identity of a user attempting to access a system. For example, passwords are commonly used to authenticate users.  
  
 **automatic partnering**  
 A setting for APPC LUs and modes that enables LU-LU pairs (with assigned modes) to be generated automatically by Host Integration Server. Each time a new APPC LU or mode is created with automatic partnering enabled, Host Integration Server searches for existing LUs and modes that also have automatic partnering enabled. Host Integration Server then uses all available automatic partners to create as many unique LU-LU pairs as possible, each pair containing a remote LU, local LU, and assigned mode. Disabling an automatic partner setting after an LU or mode has been created does not remove that LU or mode from LU-LU pairs already generated.  
  
 **automatic transaction**  
 A transaction that is created by the COM+ run-time environment for an object based on the transaction attribute of a component.  
  
 **Automation**  
 Automation is COM-based technology that enables dynamic binding to COM objects at run time.  
  
 **Automation client**  
 Also called an Automation controller. An application that manipulates the objects, methods, and properties of another application (the Automation server) through Automation.  
  
 **Automation object**  
 An object that is exposed to other applications or programming tools through Automation interfaces.  
  
 **Automation server**  
 An application that enables its objects, methods, and properties to be controlled by other applications through Automation.  
  
## -B-  
 **backup configuration file**  
 An extra copy of the configuration file, saved by using the **File** menu **BackupConfiguration** command in SNA Manager. The default extension for backup configuration file names is .SNA.  
  
 **backup server**  
 A computer running Host Integration Server, and designated as a backup server, on which the configuration file is replicated by Host Integration Server. Host Integration Server loads the copy of the configuration file located on a backup server if the primary server goes down. One or more computers running Host Integration Server can operate as backup servers.  
  
 **Base**  
 A part of each Host Integration Server component that provides the operating environment for the core functions of that component. The Base passes messages between components and provides functions common to all components, such as diagnostic tracing.  
  
 **base client**  
 A client that runs outside the COM+ run-time environment, but that instantiates COM+ objects.  
  
 **base process**  
 An application process in which a base client executes. A base client runs outside the COM+ run-time environment and instantiates COM+ application objects.  
  
 **basic conversation**  
 In APPC, a conversation type generally used by applications that provide services to other local applications. Basic conversations provide a greater degree of control over the transmission and handling of data than mapped conversations. *See also***mapped conversation**.  
  
 **basic transmission unit (BTU)**  
 A standard unit of information transmitted over an SNA network. A BTU consists of the transmission header (TH), the request/response header (RH), and the request/response unit (RU). The maximum size of the BTU is controlled in VTAM by the MAXDATA= parameter and in Host Integration Server by the Max BTU Length parameter.  
  
 **batch job**  
 A predefined sequence of programs that can be run through the Job Entry Subsystem or through an automated scheduling system. Each program that runs as part of the sequence is considered a batch step. Typically data is passed from one step to the next through temporary or permanent files on the file system.  
  
 **batch step**  
 An application program that is executed as part of a larger batch job. Typically, data is read from and written to temporary or permanent files on the files systems.  
  
 **BBI**  
 *See* **begin bracket indicator (BBI)**.  
  
 **BBIUI**  
 *See* **begin basic information unit indicator (BBIUI)**.  
  
 **BCI**  
 *See* **begin chain indicator (BCI)**.  
  
 **begin basic information unit indicator (BBIUI)**  
 Bit 5 of Flag 2 of a Status-Control message. BBIUI is set on a Status-Control message corresponding to an outbound SNA request with BBIU (begin basic information unit). It is supplied solely for the use of SNA server components. Your application should not attempt to use it.  
  
 **begin bracket indicator (BBI)**  
 Bit 4 of Flag 1 of a Status-Control message. BBI is set if the chain carries BB (begin bracket). Note that this does not necessarily indicate that the bracket has been initiated.  
  
 **begin chain indicator (BCI)**  
 Bit 1 of Flag 1 of a Status-Control message. BCI is set if the message starts a chain.  
  
 **blocking**  
 A method of operation in which a program that issues a call does not regain control until the call completes. *See also***synchronous verb completion**.  
  
 **Boolean expression**  
 An expression that can be evaluated either true (nonzero) or false (0). You can use the keywords True and False to supply the values of -1 and 0, respectively. The field data type Yes/No is Boolean and has the value of -1 for Yes and 0 for No.  
  
 **bounded**  
 Refers to recordsets or arrays. The last input parameter or the last output parameter in a method can be bounded. This means its actual size can vary from zero to the maximum number of elements (in an array) or rows (in a recordset) specified at design time.  
  
 **bracket**  
 A chained set of RUs and their responses, which together make up a transaction between two LUs. One bracket must be finished before another can be started.  
  
 **BTU**  
 *See* **basic transmission unit (BTU)**.  
  
 **business rule**  
 The combination of validation edits, logon verifications, database lookups, policies, and algorithmic transformations that constitute an enterprise's way of doing business. Also known as business logic.  
  
 **byte**  
 A unit of information consisting of eight bits. A byte, or binary term, is the smallest collection of bits that can be accessed directly. The integer value of a byte can range from 0 to 255.  
  
## -C-  
 **caller**  
 A client that invokes a method of an object. The caller of an object is not necessarily the creator of an object. For example, client A could create object X and pass this reference to client B, and then client B could use that reference to call a method of object X. In this case, client A is the creator, and client B is the caller. *See also***creator**.  
  
 **catalog**  
 In Windows, the catalog is the COM+ application data store that maintains configuration information for components, COM+ applications, and roles. You can administer the catalog by using TI Manager.  
  
 **CDI**  
 *See* **change direction indicator (CDI)**.  
  
 **CEI**  
 *See* **chain ending indicator (CEI)**.  
  
 **chain**  
 A series of related messages or data packets that are transmitted consecutively and are treated as a single entity forming a complete message.  
  
 **change direction indicator (CDI)**  
 Bit 6 of Flag 1 of a Status-Control message. CDI is set if chain carries change direction (CD).  
  
 **Channel**  
 A channel-attached connection to a host system.  
  
 **characteristics**  
 A set of internal values maintained by CPI-C for each conversation. They can affect the operation of the entire conversation or of specific calls.  
  
 **CICS**  
 *See* **Customer Information Control System (CICS)**.  
  
 **class**  
 A type that defines the interface of a particular type of object. A class defines the properties of the object and the methods used to control the behavior of an object.  
  
 **class factory**  
 An object that implements the **IClassFactory** interface, which enables it to create objects of a specific class.  
  
 **class ID (CLSID)**  
 A universally unique identifier (UUID) that identifies a COM component. Each COM component has its CLSID in the Windows registry so that it can be loaded by other applications.  
  
 **client**  
 A computer or a software component using services available through Host Integration Server. To run applications such as a 3270 emulator, the client uses the Host Integration Server computer to gain access host or peer systems on the SNA or TCP/IP network.  
  
 **client/server**  
 A distributed application model in which client applications request services from a server application. A server can have many clients at the same time, and a client can request data from multiple servers. An application can be both a client and a server.  
  
 **CLSID**  
 *See* **class ID (CLSID)**.  
  
 **coaxial cable**  
 A cable that consists of a conductor within another conductor, with insulation between the two conductors. The inner conductor is usually a small copper tube or wire, and the outer conductor is usually copper tubing or copper braid. It is the common medium used to connect LANs and 3270 devices. The maximum distance that a coaxial cable can be run between a 3270-type cluster controller and peripheral devices is 5,000 feet (1,500 meters).  
  
 **code page**  
 A table that associates specific ASCII or EBCDIC values with specific characters.  
  
 **COM**  
 *See* **Component Object Model (COM)**.  
  
 **COM+**  
 *See* **Component Services (COM+) component**; **Component Services (COM+) object**.  
  
 **COMMAREA**  
 An area of memory in the mainframe used for communications and accessible to various programs. It is similar to a data structure that contains both input parameters and return data.  
  
 **Common Programming Interface for Communications (CPI-C)**  
 A set of C-language routines that applications distributed across an SNA network can use to work together. Through CPI-C, distributed applications on computers communicating as peers can exchange data to accomplish a processing task, such as querying a remote database or copying a remote file.  
  
 An evolving application programming interface (API), embracing functions to meet the growing demands from different application environments and to achieve openness as an industry standard for communications programming. CPI-C provides access to interprogram services such as (a) sending and receiving data, (b) synchronizing processing between programs, and (c) notifying a partner of errors in the communication.  
  
 **Common Service Verb (CSV)**  
 An application programming interface (API) that provides ways of tracing, translating characters, and sending network management information to a host. Each verb supplies parameters to CSV.  
  
 **communications controller**  
 A device that directs the transmission of data over a network (for example, the IBM 3725 front-end processor).  
  
 **COMP-1**  
 Specified for internal floating-point items (single precision). The items are four bytes long. The sign is contained in the first bit of the leftmost byte, and the exponent is contained in the remaining seven bits of that byte. The last three bytes contain the mantissa.  
  
 **COMP-2**  
 Specified for internal floating-point items (double precision). The items are eight bytes long. The sign is contained in the first bit of the leftmost byte, and the remaining seven bits of that byte contain the exponent. The remaining seven bytes contain the mantissa.  
  
 **COMP-3**  
 Specified for internal decimal items. In storage, these items appear in packed decimal format. There are two digits for each character position (byte), except for the trailing character position (byte), which is occupied by the low-order digit and sign. The item can contain only the digits 0 through 9, plus a sign (in the last position), representing a value not exceeding 29 decimal digits (15 bytes).  
  
 **component**  
 A discrete unit of code built on Component Object Model or .NET Framework that delivers a specified set of services through specific interfaces. The objects are provided through the components that clients request at run time.  
  
 **Component Object Model (COM)**  
 An open architecture for cross-platform development of client/server applications based on object-oriented technology. Clients have access to an object through the interfaces implemented on the object. COM is language-neutral, so any language that produces COM components can also produce COM applications.  
  
 **Component Services (COM+) component**  
 A Component Object Model (COM) component that executes in the COM+ run-time environment. A COM+ component is commonly known as a COM+ application. A COM+ component must be a dynamic-link library (.dll) file that implements a class factory to create objects and that describes all of the interfaces of the component in a type library to facilitate standard marshaling.  
  
 **Component Services (COM+) object**  
 A Component Object Model (COM) object that executes in the COM+ run-time environment.  
  
 **concurrency**  
 The appearance of simultaneous execution of processes or transactions by interleaving the execution of multiple pieces of work.  
  
 **configuration file**  
 A file containing setup and configuration information for Host Integration Server. It defines servers, connections, LUs, users, and other items. The configuration file that is loaded when SNA Manager starts is called COM.CFG.  
  
 **connection**  
 The data communication path between a workstation or server and other computers on the SNA network. Host Integration Server offers a variety of connection types:  
  
- 802.2 (Token Ring or Ethernet)  
  
- Synchronous Data Link Control (SDLC)  
  
- X.25  
  
- Distributed function terminal (DFT)  
  
- Channel  
  
- Twinax  
  
  **connection object**  
  In AFTP, a connection (not necessarily active) to a partner computer.  
  
  **connectivity**  
  (1) The capability of a system or device to be attached to other systems or devices without modification. (2) The capability to attach a variety of functional units without modifying them.  
  
  **connectivity option**  
  A type of connection hardware and software through which one computer communicates with other computers.  
  
  **consistency**  
  A state in which durable data matches the state expected by the business rules that modified the data.  
  
  **constructor**  
  In C, a special initialization function that is called automatically whenever an instance of a class is declared. This function prevents errors that result from the use of uninitialized objects. The constructor has the same name as the class itself and cannot return a value.  
  
  **contention loser**  
  In an APPC LU-LU session, the LU that cannot start a conversation with its partner LU (the contention winner) without first requesting permission of the partner LU. *See also***contention winner**.  
  
  **contention winner**  
  In an APPC LU-LU session, the LU that can start a conversation with its partner LU (the contention loser). If parallel sessions between the two LUs are being used, each LU may be the contention winner for some sessions and the contention loser for other sessions. *See also***contention loser**.  
  
  **context**  
  The state that is implicitly associated with a given COM+ object. The context contains information about the execution environment of an object, such as the identity of the creator of an object and, optionally, the transaction encompassing the work of the object. The context of an object is similar in concept to the process context that an operating system maintains for an executing program. The COM+ run-time environment manages a context for each object.  
  
  **control point**  
  A node or other SNA component that controls network resources and coordinates the activation of sessions.  
  
  **controller**  
  A device that directs the transmission of data over a network (for example, the IBM 3725 front-end processor).  
  
  **conversation**  
  The process used by network-based applications to communicate with each other and to exchange data to accomplish processing tasks. (1) A logical connection between two transaction programs using an LU 6.2 session. Conversations are delimited by brackets to gain exclusive use of a session. (2) The interaction between TPs carrying out a specific task. Each conversation requires an LU-LU session. A TP can be involved in several conversations simultaneously. *See also* **basic conversation**; **mapped conversation**.  
  
  **conversation characteristics**  
  Internal API values that define the overall operation for a conversation or for a specific call. *See also***application programming interface (API)**; **conversation**.  
  
  **conversation ID**  
  A unique identifier for a conversation between two transaction programs (TPs).  
  
  **CPI-C**  
  *See* **Common Programming Interface for Communications (CPI-C)**.  
  
  **creator**  
  A client that creates an object provided by a component (using **CreateObject**, **CoCreateInstance**, or the **CreateInstance** method). When a client creates an object, it is given an object reference that can be used to call the methods of that object. *See also***caller**.  
  
  **CSV**  
  *See* **Common Service Verb (CSV)**.  
  
  **Currency**  
  An 8-byte, fixed-point data type that is useful for calculations involving money or for fixed-point calculations in which accuracy is extremely important. This data type is used to store numbers with up to 15 digits to the left of the decimal point and 4 digits to the right. The type-declaration character in Microsoft® Visual Basic® is an at sign (@). Currency can range from –922,337,203,685,477.5808 to 922,337,203,685,477.5807.  
  
  **current directory**  
  The first directory in which the operating system looks for programs and data files and stores files for output.  
  
  **Customer Information Control System (CICS)**  
  An IBM transaction processing program that provides an environment on IBM mainframes in which applications can communicate with terminals or other applications.  
  
## -D-  
 **DACTLU**  
 An SNA command that is sent to deactivate the session between the system services control point (SSCP) and a logical unit (LU).  
  
 **DACTPU**  
 An SNA command that is sent to deactivate the session between the system services control point (SSCP) and a physical unit (PU).  
  
 **data link control (DLC)**  
 In SNA, the protocol stack layer that transmits messages across links and manages link-level flow and error recovery.  
  
 **data set members**  
 Members of partitioned data sets that are individually named elements of a larger file that can be retrieved by name.  
  
 **database**  
 (1) A collection of data with a given structure for accepting, storing, and providing on demand data for multiple users. (2) A collection of interrelated data organized according to a database schema to serve one or more applications. (3) A collection of data fundamental to a system. (4) A collection of data fundamental to an enterprise.  
  
 **Date**  
 An 8-byte, real data type used to store dates and times as a real number. Variables are stored as 64-bit numbers. The value to the left of the decimal represents a date, and the value to the right of the decimal represents a time. The Date data type can range from January 1, 1000 to December 31, 9999.  
  
 **DCOM**  
 *See* **distributed COM (DCOM)**.  
  
 **DDM**  
 *See* **distributed data management (DDM)**.  
  
 **deallocate**  
 (1) The process an operating system uses to free memory that has been previously allocated by a program. (2) In Advanced Program-to-Program Communications (APPC), a verb that ends a conversation. *Contrast with***allocate**.  
  
 **Decimal**  
 A data type that stores a signed, exact numeric value described as the number of digits appearing before and after the decimal point, with a maximum of 29 total digits. All possible digits cannot be represented if you are using the maximum number of digits.  
  
 **default**  
 The value that is automatically used if nothing is specified.  
  
 **dependent local APPC LU**  
 A local logical unit (LU) that enables Advanced Program-to-Program Communications (APPC) with a peer system, but only through a host (mainframe) system. The type of LU used in dependent APPC is LU 6.2.  
  
 **DFT**  
 *See* **distributed function terminal** (**DFT)**.  
  
 **digit**  
 In COBOL, any of the numerals from 0 through 9 not used in reference to any other symbol.  
  
 **direct caller**  
 The identity of the process (base client or server process) calling into the current server process.  
  
 **direct creator**  
 The identity of the process (base client or server process) that directly created the current object.  
  
 **directory**  
 (1) A list of files that are stored on a disk or diskette. A directory also contains information about the files such as size and date of last change. (2) A named grouping of files in a file system.  
  
 **display emulation**  
 A feature that enables a personal computer to emulate an IBM 3278 or 3279 terminal. *See also***emulation**.  
  
 **display model**  
 One of several different sizes of display:  
  
- Model 2 is 24 lines by 80 characters  
  
- Model 3 is 32 lines by 80 characters  
  
- Model 4 is 43 lines by 80 characters  
  
- Model 5 is 27 lines by 132 characters  
  
  **display session**  
  A 3270 emulation session between a networked personal computer and a host. The session is used to emulate a 3278 or 3279 display. Also called a host display session.  
  
  **DISPLAY verb**  
  An APPC verb that returns configuration information and current operating values for a computer running Host Integration Server.  
  
  **distributed COM (DCOM)**  
  An object protocol that enables COM components to communicate directly with each other across a network. Because DCOM is language-neutral, any language that uses COM components can also produce DCOM applications.  
  
  **distributed data management (DDM)**  
  A function of the operating system that enables an application program or user on one system to use database files stored on remote systems. A communications network must connect the systems, and the remote systems must also be using DDM.  
  
  **distributed function terminal**( **DFT)**  
  A type of intelligent terminal supported by IBM 3270 control units, in which some of the terminal's functions are controlled by the terminal and some by the control unit. Enables multiple sessions, and connects to host systems or to peer systems through host systems. DFT terminals are often connected using coaxial cable.  
  
  **distributed processing**  
  A form of information processing in which the work is performed by separate computers that are linked through a local or wide area network, using data-transfer mechanisms that enable different programs to use and share data.  
  
  **distributed program call (DPC)**  
  An AS/400 remote communication model.  
  
  **Distributed Query Processor (DQP)**  
  Enables queries to access multiple data sources on multiple servers, even SQL and DB2, and combine views, create data warehouses, and so on. DQP supports an extended version of the SQL language that permits users to qualify table names with the databases in which they exist. This gives users the capability to formulate queries that span multiple distributed databases.  
  
  **Distributed Relational Data Architecture (DRDA)**  
  A connection protocol for distributed relational database processing that is used by IBM relational database products. The DRDA protocol comprises protocols for communication between an application and a remote database, and communication between databases. The DRDA protocol provides the connections for remote and distributed processing. The DRDA protocol is built on the Distributed Data Management Architecture.  
  
  **Distributed Transaction Coordinator (DTC)**  
  A transaction manager that coordinates transactions spanning multiple resource managers. Work can be committed as an atomic transaction even if it spans multiple resource managers, even on separate computers.  
  
  **distributed unit of work (DUW)**  
  In DB2 UDB for AS/400, this is a method of accessing distributed relational data in which a user or application can, within a single unit of work, read and update data on multiple database management systems (DBMSs). The user or application directs each SQL statement to a particular DBMS for execution at the DBMS. Each SQL statement may access only one DBMS.  
  
  **DL-BASE**  
  The type of Base used by Host Integration Server 3270 emulation programs. It supports a single Host Integration Server component or a single user application and has entry points for initialization, sending messages, receiving messages, and termination. *See also***Base**.  
  
  **DLC**  
  *See* **data link control (DLC)**.  
  
  **DLL**  
  *See* **dynamic-link library (DLL)**.  
  
  **DMOD**  
  *See* **Dynamic Access Module (DMOD)**.  
  
  **document type definition (DTD)**  
  Can accompany a document, essentially defining the rules of the document, such as which elements are present and the structural relationship between the elements. It defines what tags can go in your document, what tags can contain other tags, the number and sequence of the tags, the attributes your tags can have, and optionally, the values those attributes can have.  
  
  DTDs help to validate the data when the receiving application does not have a built-in description of the incoming data. The DTD is declared within the document type declaration production of the XML file. With XML, however, DTDs are optional.  
  
  **downstream connection**  
  A connection that enables a computer running Host Integration Server to support communication between hosts and clients. Even though such clients do not use the Host Integration Server client/server interface, with a downstream connection they can access host connections available through a computer running Host Integration Server.  
  
  Host Integration Server offers several types of downstream connection:  
  
- 802.2 (Token Ring or Ethernet)  
  
- SDLC  
  
- X.25  
  
  **downstream LU**  
  A logical unit (LU) used by clients to access a host connection through a computer running Host Integration Server. Such clients do not use the Host Integration Server client/server interface, but by using a downstream LU, can receive access to connections on a computer running Host Integration Server. A downstream LU uses a downstream connection, and passes information between the client and the host.  
  
  **downstream system**  
  A client such as an IBM Communications Manager/2 system that can access host connections available on a computer running Host Integration Server. Even though such clients do not use the Host Integration Server client/server interface, they can use a downstream connection and a downstream LU to communicate with the host through Host Integration Server. Host Integration Server passes the information between the downstream system and the host. With Host Integration Server, downstream systems appear to the host as logical units, not physical units.  
  
  **DPC**  
  *See* **distributed program call (DPC)**.  
  
  **DPL-enabled**  
  Compatible with the IBM Distributed Program Link (DPL) protocol.  
  
  **DQP**  
  *See* **Distributed Query Processor (DQP)**.  
  
  **DRDA**  
  *See* **Distributed Relational Data Architecture (DRDA)**.  
  
  **DTC**  
  *See* **Distributed Transaction Coordinator (DTC)**.  
  
  **DTD**  
  *See* **document type definition (DTD)**.  
  
  **duplex**  
  Capable of simultaneously transmitting and receiving data. Also called **full-duplex** or **4-wire**. *Contrast with***half-duplex**.  
  
  **durability**  
  A state that survives failures.  
  
  **DUW**  
  *See* **distributed unit of work (DUW)**.  
  
  **Dynamic Access Module (DMOD)**  
  An SNA component that provides the communications facilities needed to pass messages between the Bases.  
  
  **dynamic-link library (DLL)**  
  A binary file that contains one or more functions that are compiled, linked, and stored separately from the processes that use them. The operating system maps a DLL to the address space of the calling process when the process starts or while it is running. It uses the .dll file extension.  
  
## -E-  
 **EBCDIC**  
 *See* **Extended Binary Coded Decimal Interchange Code (EBCDIC)**.  
  
 **EBI**  
 *See* **end bracket indicator (EBI)**.  
  
 **EBIUI**  
 *See* **end basic information unit indicator (EBIUI)**.  
  
 **ECI**  
 *See* **end chain indicator (ECI)**.  
  
 **ELM**  
 *See* **enhanced listener message (ELM)**.  
  
 **emulation**  
 A process whereby one device imitates another; for example, a personal computer can emulate a 3278 terminal. *See also***display emulation**.  
  
 **end bracket indicator (EBI)**  
 Bit 5 of Flag 1 of a Status-Control message. Set if chain carries end bracket (EB). Note that this does not indicate that the bracket has terminated.  
  
 **end chain indicator (ECI)**  
 Bit 2 of Flag 1 of a Status-Control message. Set if this message ends a chain.  
  
 **enhanced listener message (ELM)**  
 A streamlined, application-level protocol exchange sequence that sends to and receives from the host application a single data stream composed of a header followed by the application data.  
  
 **ERI**  
 *See* **exception response indicator (ERI)**.  
  
 **Ethernet**  
 An IEEE 802.3 standard for contention networks. Ethernet uses a bus or star topology and relies on the form of access known as Carrier Sense Multiple Access with Collision Detection (CSMA/CD) to regulate communication line traffic. Network nodes are linked by coaxial cable, by fiber-optic cable, or by twisted-pair wiring. Data is transmitted in variable-length frames containing delivery and control information and up to 1,500 bytes of data. The Ethernet standard provides for baseband transmission at 10 megabits per second.  
  
 **event log**  
 Host Integration Server records events involving communications hardware (for example, communications adapters) or software in the Windows Event Log. Events can include attempts to establish communication, successful establishment of sessions, failures of system components, attempts to use files that are damaged or missing, configuration problems, and responses from remote systems.  
  
 **exception**  
 An abnormal condition or error that occurs during the execution of a program and that requires the execution of software outside the normal flow of control.  
  
 **exception request (EXR)**  
 A request in which an intermediate component has detected an error and modified the request so the final destination is also aware of the error.  
  
 **exception response indicator (ERI)**  
 A specified response for a request. The response should be issued only if the request cannot be processed or if an error was encountered during processing.  
  
 **exchange identification (XID)**  
 An identifier that is exchanged between nodes on an SNA network, and that enables the nodes to recognize each other and to establish link and node characteristics for communicating. With Host Integration Server, there are two possible kinds of XIDs that can be exchanged: Format 0 XIDs (containing only basic information such as Node ID) and Format 3 XIDs (containing more detailed information such as Network Name and Control Point Name). *See also***Format 0 XID**; **Format 3 XID**.  
  
 **EXR**  
 *See* **exception request (EXR)**.  
  
 **Extended Binary Coded Decimal Interchange Code (EBCDIC)**  
 A coding scheme developed by IBM for use with its mainframe and AS400 computers as a standard method of assigning binary (numeric) values to alphabetic, numeric, punctuation, and transmission-control characters.  
  
 **Extensible Markup Language (XML)**  
 A specification developed by the World Wide Web Consortium (W3C) that enables designers to create customized tags beyond the capabilities of standard Hypertext Markup Language (HTML). While HTML uses only predefined tags to describe elements within the page, XML enables tags to be defined by the developer of the page. Tags for virtually any data item, such as a product or an amount due, can be used for specific applications. This enables Web pages to function as database records.  
  
 **Extensible Stylesheet Language (XSL)**  
 A style sheet format for Extensible Markup Language (XML) documents. XSL is used to define the display of XML in the same way that cascading style sheets (CSS) are used to define the display of Hypertext Markup Language (HTML).  
  
## -F-  
 **fault isolation**  
 Containing the effects of a fault within a component, rather than propagating the fault to other components in the system.  
  
 **fault tolerance**  
 The ability of a system to recover from an error, a failure, or a change in environmental conditions (such as loss of power). True fault tolerance provides for fully automatic recovery without disruption of user tasks or files, in contrast to manual means of recovery such as restoring data loss with backup files.  
  
 **file transfer**  
 The process of sending and receiving data files to and from computers.  
  
 **fill type**  
 A value that indicates whether programs will receive data in the form of logical records or as a specified length of data.  
  
 **flow**  
 A verb flows from one LU to another.  
  
 **FMHI**  
 *See* **function management header indicator (FMHI)**.  
  
 **FMI**  
 *See* **function management interface (FMI)**.  
  
 **Format 0 XID**  
 A type of XID that supplies minimal information about the node. Format 0 XIDs have a fixed length. They can be used for 3270 and LUA communication, and cannot be used for Advanced Program-to-Program Communications (APPC). *See also***exchange identification (XID)**, **Format 3 XID**.  
  
 **Format 3 XID**  
 A type of XID that supplies more detailed information about the node than a Format 0 XID. Format 3 XIDs have a variable length. They can be used for 3270 and LUA communication, and are the only type of XID that can be used for Advanced Program-to-Program Communications (APPC). *See also***exchange identification (XID)**; **Format 0 XID**.  
  
 **full-duplex**  
 Capable of simultaneously transmitting and receiving data. Also called **duplex** or **4-wire**. *Contrast with***half-duplex**.  
  
 **full-duplex transmission**  
 Two-way electronic communication that takes place in both directions simultaneously. Also called **duplex transmission** or **4-wire transmission**. *Contrast with***half-duplex transmission**.  
  
 **fully qualified LU name**  
 The two-part network address (network.lu) that uniquely identifies a destination (typically a user) in the network.  
  
 **function management header indicator (FMHI)**  
 Headers inserted into requests containing end-user data to convey control information.  
  
 **function management interface (FMI)**  
 An interface that provides applications with direct access to SNA data flow and information about SNA control flows by means of status messages. It is particularly suited to the requirements of 3270 emulation applications.  
  
## -G-  
 **GAC**  
 *See* **global assembly cache (GAC)**.  
  
 **global assembly cache (GAC)**  
 A machine-wide code cache that stores assemblies specifically installed to be shared by many applications on the computer. Applications deployed in the global assembly cache must have a strong name.  
  
 **group**  
 A set of one or more Windows user accounts.  
  
## -H-  
 **half-duplex**  
 Capable of only one direction of communication at a time, either receiving data or transmitting data, but not doing both at the same time. Also called **2-wire**. *Contrast with***full-duplex**.  
  
 **half-duplex transmission**  
 Two-way electronic communication that takes place in only one direction at a time. Also called **2-wire transmission**. *Contrast with***full-duplex transmission**.  
  
 **HE**  
 *See* **host environment (HE)**.  
  
 **HIDX**  
 Host Integration Designer XML (HIDX) metadata file is used for encoding and decoding records in mainframe z/OS, midrange i5/OS and offline host files using Microsoft ADO.NET Provider for Host Files and Microsoft BizTalk Adapter for Host Files.  
  
 **high-level language application programming interface (HLLAPI)**  
 An API that enables you to develop and run programmer-operator applications on IBM personal computers (or compatibles) that communicate with IBM mainframes using 3270 emulation.  
  
 **HIP**  
 *See* **host-initiated processing (HIP)**.  
  
 **HLLAPI**  
 *See* **high-level language application programming interface (HLLAPI)**.  
  
 **host environment (HE)**  
 An object that defines the network and hardware characteristics of the non-Windows software platform that initiates requests to the Windows platform. The host environment consists of the host environment name, host identification, network transport type, data conversion information, default method resolution criteria, and security credential mapping.  
  
 **Host Integration Server**  
 A Microsoft® software program that enables a personal computer to communicate with remote computers such as IBM mainframes, AS/400s, or other personal computers on a TCP/IP or SNA network.  
  
 **host response time**  
 The amount of time that a host computer takes to reply to a message sent to it by a client computer. Host response time is measured from the moment that the personal computer sends the message until one of the following events: the client computer receives data back from the host, the host unlocks the client computer's keyboard, or the host enables the client computer to send more data.  
  
 **host system**  
 A computer system (usually a mainframe) that controls interactions between it and the computers connected to it. A host system makes operating systems and applications available by way of Host Integration Server to computers running software for terminal emulation or for APPC.  
  
 In SNA terminology, a host is capable of sending an ACTPU command to Host Integration Server and sets up a PU-SSCP session with Host Integration Server.  
  
 **host-addressable printer**  
 A printer that is defined as a device associated with a logical unit (LU) configured as LU type 1 or 3 and that can support host printing as well as local printing.  
  
 **host-initiated processing (HIP)**  
 A non-Microsoft software platform (usually a mainframe or mid-range computer such as the AS/400) that can access and integrate its programs with the programs on a Windows server platform.  
  
 **hot backup**  
 (1) The ability to take systems online and offline without disrupting service. (2) A configuration in which one resource (such as a server running Host Integration Server software) can automatically handle sessions if another cannot. Such servers can provide hot backup for 3270, LUA, or downstream sessions through pools containing LUs from multiple servers. Servers running Host Integration Server software can provide hot backup for 5250 terminal emulation through the use of LU names that are the same on multiple servers.  
  
## -I-  
 **I-frame**  
 *See* **Information frame (I-frame)**.  
  
 **identity**  
 A COM+ application property page that specifies the user accounts authorized to use that application. You can set it to **Interactive user** (to authorize the current logged on user), to a specific user account, or to a group of users within a Windows domain.  
  
 **IEEE**  
 *See* **Institute of Electrical and Electronics Engineers (IEEE)**.  
  
 **implicit incoming mode**  
 A mode that defines the properties to use when Host Integration Server receives a request to start a session, and the mode named in the request is not recognized by Host Integration Server. An implicit incoming mode enables greater flexibility in starting sessions with remote systems.  
  
 For a session to be established, the incoming local LU name must be recognized by Host Integration Server. Then, the incoming remote LU must either be recognized explicitly or handled implicitly (if an implicit incoming remote LU has been configured). If the remote LU is recognized explicitly, but the mode is not recognized (as part of an LU-LU pair), Host Integration Server internally creates a new mode definition with the correct name, using the properties of the implicit incoming mode. Alternatively, if the remote LU is handled implicitly, Host Integration Server also handles the mode implicitly, by internally creating a mode, as described.  
  
 Note that an implicit incoming mode must be configured for any remote LU that will be used as an implicit incoming remote LU. An implicit incoming mode can be (but does not have to be) configured for remote LUs that will only be used explicitly.  
  
 **implicit incoming remote LU**  
 A remote APPC LU that defines the properties to use when Host Integration Server receives a request to start a session with a local LU, and the remote LU named in the request is not recognized by Host Integration Server. An implicit incoming remote LU that enables greater flexibility in starting sessions with remote systems.  
  
 Note that for a session to be established, the local LU name must be recognized by Host Integration Server. If the local LU name is recognized, but the remote LU name is not recognized as a partner for the local LU, Host Integration Server internally creates a new remote LU definition with the correct name, using the properties of the implicit incoming remote LU.  
  
 In SNA Manager, before a remote APPC LU can be used as an implicit incoming remote LU, an implicit incoming mode must be configured for it.  
  
 **IMS**  
 *See* **Information Management Systems (IMS)**.  
  
 **independent local APPC LU**  
 A local logical unit (LU) that enables Advanced Program-to-Program Communications (APPC) with a peer system without involving a host (mainframe) system. The type of LU used in independent APPC is LU 6.2. An independent LU does not require a host system, but can work through one.  
  
 **IND$FILE**  
 IBM file transfer program that enables files to be transferred from a personal computer to the host and from the host to the personal computer. It operates in three host environments: CICS, VM/CMS, and MVS/TSO.  
  
 **Information frame (I-frame)**  
 A standard unit of information transmitted over an SNA network. For 802.2 or SDLC communication, an I-frame is equivalent to a BTU. *See also***basic transmission unit (BTU)**.  
  
 **Information Management Systems (IMS)**  
 A transaction processing monitor created and sold by IBM Corporation.  
  
 **in-process component**  
 A component that runs in a client's process space. This is typically a dynamic-link library (DLL).  
  
 **instance**  
 An object of a particular component class. Each instance has its own private data elements or member variables. A component instance is synonymous with object.  
  
 **Institute of Electrical and Electronics Engineers (IEEE)**  
 An organization that maintains the standards for the 802.x protocols used in communications on local area networks.  
  
 **Integer**  
 A fundamental Automation data type that holds integer numbers. An integer variable is stored as a 16-bit (2-byte) number ranging in value from –32,768 to 32,767. The type-declaration character is a percent sign (%) (ANSI character 37). In Microsoft® Visual Basic®, you can use integers to store Boolean (**True**/**False**) values.  
  
 **interface**  
 A group of logically related operations or methods that provides access to a component object.  
  
 **Internet Protocol (IP) routed network**  
 A TCP/IP wide area network in which IP packets are propagated across the network through devices called IP routers.  
  
 **invokable**  
 Indicates the capability of a program to be started by another program. For example, an invokable APPC transaction program (TP) can be started in response to a request from another TP (the invoking TP).  
  
 **invoked program**  
 A program that has been activated by a call or verb. *See also***invoking program**.  
  
 **invoked TP**  
 A host transaction program (TP) started by:  
  
- Another (the invoking) TP.  
  
- A Transaction Integrator Automation server working in conjunction with the TI run-time environment and Microsoft Distributed Transaction Server (DTS) included in COM+.  
  
  **invoking program**  
  A program that uses a call or verb to activate another program. Also known as the calling program or the client. *See also***invoked program**.  
  
  **invoking TP**  
  A TP that initiates a conversation with another TP. The invoking TP starts the other TP by instructing the remote node to load the invokable TP.  
  
  **IP routed network**  
  *See* **Internet Protocol (IP) routed network**.  
  
  **isolation**  
  A characteristic whereby two transactions running in parallel produce the illusion that there is no concurrency. It appears that the system is running one transaction at a time.  
  
## -J-  
 No terms.  
  
## -K-  
 No terms.  
  
## -L-  
 **LAN**  
 *See* **local area network (LAN)**.  
  
 **LE**  
 *See* **local environment (LE)**.  
  
 **leased SDLC line**  
 A dedicated telecommunications line using SDLC. *See also***Synchronous Data Link Control (SDLC)**.  
  
 **link service**  
 The software component of Host Integration Server that communicates with the device driver for a particular communication adapter (802.2, SDLC, X.25, DFT, Channel, or Twinax).  
  
 **listener**  
 A local environment associated with an application, where the local environment monitors the TCP/IP or SNA network for requests to the application.  
  
 **load balancing**  
 Distribution of the processing load among several servers carrying out network tasks to increase overall network performance.  
  
 **local account**  
 An account provided in a local domain for a user whose regular account is not in a trusted domain. Local accounts cannot be used to log on interactively. Local accounts created in one domain cannot be used in trusted domains.  
  
 **local area network (LAN)**  
 A high-speed communication system consisting of hardware (computers and peripherals) and software (programs and data files) that are interconnected by cable in a way that enables these resources to be shared. The connected devices are located within a limited geographic area such as a building or campus.  
  
 **local environment (LE)**  
 An object that defines the endpoint on a Windows computer that accepts incoming requests from a non-Windows software platform. The local environment consists of the local environment name, network transport type, network transport class, and endpoint identification.  
  
 **local LU**  
 In an APPC or CPI-C conversation, the logical unit (LU) on the local end. *Contrast with***partner LU** and **remote LU**.  
  
 **local LU alias**  
 The name by which a local logical unit (LU) is known to the local transaction program (TP).  
  
 **local node**  
 The software component of Host Integration Server that interacts with clients and other nodes on the SNA network.  
  
 **local printer**  
 A printer that is attached directly to a personal computer.  
  
 **local program**  
 In CPI-C, the program on the local end of the conversation. *Contrast with* partner program.  
  
 **local TP**  
 In an Advanced Program-to-Program Communications (APPC) or Common Programming Interface for Communications (CPI-C) conversation, the transaction program (TP) on the local end. *Contrast with***partner TPs** and **remote transaction program**. *See also***local LU**.  
  
 **locality**  
 A base and the components within it; that is, a Host Integration Server executable program.  
  
 **locality, partner, index (LPI)**  
 An LPI address that is used to identify each end of a connection. It has three components: locality (L), partner (P), and index (I).  
  
 **logical unit (LU)**  
 (1) A type of network-accessible unit that enables users to gain access to network resources and communicate with each other. (2) A preset unit containing all of the configuration information needed for a user, program, or downstream system to establish a session with a host or peer computer. *See also***LU alias**; **LU name**; **LU pool**.  
  
 **logical unit application (LUA)**  
 A conventional LU application, or the interface that these applications use. LUA enables workstations to communicate with host applications using LU 0, 1, 2, or 3 protocols.  
  
 **LPI**  
 *See* **locality, partner, index (LPI)**.  
  
 **LPI address**  
 Used to identify each end of a connection between two partners. It can have three components: L identifies the locality, P identifies the partner within the locality, and I identifies a logical entity within the partner. *See also***locality**; **partner**.  
  
 **LU**  
 *See* **logical unit (LU)**.  
  
 **LU alias**  
 A string that identifies an APPC or CPI-C logical unit (LU) to transaction programs (TPs) in the same organizational unit (OU). An LU alias is used only locally by Host Integration Server, but it also can be used by any program in the OU of the host mainframe system. *See also***LU name**.  
  
 **LU name**  
 For 3270 or LUA communication, a name that identifies a logical unit (LU). For independent APPC or CPI-C, a name that (when used with the network name) identifies an LU to other components on an SNA network. For dependent APPC or CPI-C, a name that identifies an LU to local software, such as the Windows Event Viewer. *See also***LU alias**.  
  
 **LU pool**  
 A number of logical units (LUs) of the same type that are made available as a group. A user or LU application addressing the pool will connect to the next available LU in the pool for that session only. *See also***logical unit (LU)**.  
  
 **LU type**  
 Logical unit type. A subset of the SNA protocol that characterizes the communication between two LUs.  
  
 **LU type 0**  
 A logical-unit protocol with minimal constraints, on which special applications can be built for SNA.  
  
 **LU type 1**  
 A logical-unit protocol used by a host application communicating with a printer, sending data that conforms to the 3270 SNA Character String (SCS) definition.  
  
 **LU type 2**  
 A logical-unit protocol used by a host application communicating with a 3270-type display terminal, using the SNA 3270 data stream.  
  
 **LU type 3**  
 A logical-unit protocol used by a host application communicating with a printer, sending data that is 3270 data stream compatible (DSC).  
  
 **LU type 6.2**  
 A logical-unit protocol used by two applications or transaction programs (TPs) communicating as peers in an SNA environment. LU 6.2 works in combination with node type 2.1 to provide Advanced Program-to-Program Communications (APPC) using independent LUs. LU 6.2 also works with node type 2.0 to provide APPC with dependent LUs.  
  
 **LU-LU session**  
 A logical, two-way exchange between two logical units (LUs) over a specific connection for a specific amount of time.  
  
 **LUA**  
 *See* **logical unit application (LUA)**.  
  
## -M-  
 **MAC address**  
 A 12-byte hexadecimal address used by the media access control (MAC) layer of an 802.2 connection. It corresponds to the VTAM MACADDR= parameter and to the Remote Network Address parameter for an 802.2 connection with Host Integration Server.  
  
 **management object**  
 A TI component that manages or provides access to administration information. Typically, management objects are visible only when errors or messages are reported or placed in the Windows Event Log.  
  
 **mapped conversation**  
 A conversation in which the sending program sends one logical record at a time and the receiving program receives one record at a time. *See also* **conversation**.  
  
 **marshaling**  
 The process of packaging and sending interface method parameters across thread or process boundaries.  
  
 **member server**  
 A server that does not contain a configuration file. One or more servers can operate as member servers. The other types of servers are the primary server and backup servers.  
  
 **method**  
 A procedure (function) that acts on an object.  
  
 **Microsoft .NET**  
 Microsoft® .NET is a set of software technologies for connecting information, people, systems, and devices. This new generation of technology is based on Web services—small building-block applications that can connect to each other as well as to other, larger applications over the Internet.  
  
 **mode**  
 A collection of session properties used by LU 6.2-type logical units (LUs) as they carry on a session. A mode can be used by many LU pairs at the same time.  
  
 **mode name**  
 The name used by the initiator of a session to designate the characteristics desired for the session, such as traffic pacing values, message-length limits, Sync Point and cryptography options, and the class of service within the transport network.  
  
 **model**  
 One of several different sizes of display:  
  
- Model 2 is 24 lines by 80 characters  
  
- Model 3 is 32 lines by 80 characters  
  
- Model 4 is 43 lines by 80 characters  
  
- Model 5 is 27 lines by 132 characters  
  
  **Messaging-oriented middleware**  
  Messaging-oriented middleware (MOM) is a set of products that connects applications running on different systems by sending and receiving application data as messages. Examples are RPC, CPI-C, and message queuing.  
  
  **multidrop**  
  A connection in which one primary node communicates with multiple secondary nodes concurrently over the same physical transmission medium.  
  
  **multiple sessions**  
  In CPI-C, two or more concurrent sessions with different partner LUs. *Seealso***LU-LU session**.  
  
  **Multiple Virtual Storage (MVS)**  
  An operating system for large IBM mainframe computers. Implies MVS/370, the MVS/XA product, and the MVS/ESA product.  
  
  **MVS**  
  *See* **Multiple Virtual Storage (MVS)**.  
  
## -N-  
 **NAU**  
 *See* **network addressable unit (NAU)**.  
  
 **NC**  
 *See* **network control (NC)**.  
  
 **NCP**  
 *See* **Network Control Program (NCP)**.  
  
 **.NET Framework**  
 An integral Microsoft® Windows® component for building and running the next generation of applications and XML Web services.  
  
 **NetView**  
 A reporting system that runs on an IBM host (mainframe), forwarding alerts and other information back and forth between the host and personal computers, and other network addressable units that connect to the host.  
  
 **NetView alert**  
 A message sent to the NetView reporting system, indicating an abnormal event or a failure.  
  
 **NetView user alert**  
 A message sent by a 3270 user to a host system operator through NetView, requesting an action such as mounting a tape or changing forms on a printer. Also called user alert.  
  
 **network**  
 Computer systems, controllers, terminals, and software connected in a way that enables them to communicate with each other.  
  
 **network addressable unit (NAU)**  
 The basic functional entities in an SNA environment that are the source or destination of all information flowing within the SNA network. The NAU can be a logical unit (LU), a physical unit (PU), or a system services control point (SSCP).  
  
 **network control (NC)**  
 A set of SNA-defined requests and responses used to control explicit and virtual routing.  
  
 **Network Control Program (NCP)**  
 An IBM program that supports communication controllers in single-domain, multiple-domain, and interconnected networks.  
  
 **Network Management Vector Transport (NMVT)**  
 SNA message containing network or system management information.  
  
 **network name**  
 A name identifying an SNA network. The network name is used in combination with other identifiers, either a control point name (to identify a control point or node) or an LU name (to identify an APPC LU, particularly an independent local APPC LU). The combination of a network name with a control point name is sometimes called a network qualified control point name. The combination of a network name with an LU name is sometimes called a fully qualified network name.  
  
 **NMVT**  
 *See* **Network Management Vector Transport (NMVT)**.  
  
 **node**  
 (1) A server, controller, workstation, printer, or other processor that implements SNA functions. SNA defines three kinds of nodes: the host subarea node, which functions to control and manage a network; the communication controller subarea node, which routes and controls data flow through the network; and peripheral nodes, which include printers, workstations, cluster controllers, and distributed processors.  
  
 (2) A branch on a navigation tree.  
  
 **node type 2.1**  
 An SNA component, such as an intelligent terminal or a personal computer, that works together with LU type 6.2 to support peer-to-peer communications, allowing the logical units (LUs) to function independently from the host.  
  
 **null**  
 A value that indicates missing or unknown data.  
  
## -O-  
 **object**  
 A run-time instance of a Component Object Model (COM) component. An object is created by a component's class factory. Object is synonymous with instance.  
  
 **object variable**  
 A variable that contains a reference to an object.  
  
 **OCCURS DEPENDING ON**  
 Code syntax that specifies variable-length tables. This is the COBOL version of an array that contains a variable number of elements.  
  
 **OCCURS**   
 ***fixed times***  
 Code syntax that specifies fixed-length tables. This is the COBOL version of an array.  
  
 **open transaction management architecture (OTMA)**  
 A high-performance, connectionless protocol used by IMS to communicate efficiently with Multiple Virtual Storage (MVS) applications without using the SNA protocol.  
  
 **operator-loaded TP**  
 An invokable transaction program (TP) that is manually loaded and started by an operator.  
  
 **original caller**  
 The identity of the base client that initiates an activity.  
  
 **original creator**  
 The identity of the base client that created the current object. The original caller and original creator are different only if the original creator passed the object to a different base client. *See also***original caller**.  
  
 **OS/390**  
 The IBM operating system for the IBM S/390 family of enterprise servers and that includes and integrates functions previously provided by other IBM software products such as the MVS operating system.  
  
 **OS/400**  
 The IBM operating system for the IBM AS/400.  
  
 **OTMA**  
 *See* **open transaction management architecture (OTMA)**.  
  
 **out-of-process component**  
 A component that runs in a separate process space from its client.  
  
## -P-  
 **pacing receive count**  
 The maximum number of frames for the local logical unit (LU) to receive from the partner LU before the local LU sends a response.  
  
 **pacing send count**  
 The maximum number of frames for the local logical unit (LU) to send without receiving an SNA pacing response from the partner LU.  
  
 **packet**  
 A transmission unit of fixed maximum size, used as the basic unit on a packet-switching network. A packet contains both a header and data.  
  
 In data communication, a sequence of binary digits, including data and control signals, that is transmitted and switched as a composite whole. The data, control signals, and possibly error control information are arranged in a specific format.  
  
 **packet switching**  
 A message-delivery technique in which small units of information (packets) are relayed through stations in a computer network along the best route currently available between the source and the destination. Packet-switching networks are considered to be fast and efficient. The protocol used on packet-switching networks is X.25. *See also* **X.25**.  
  
 **parallel sessions**  
 Multiple concurrent sessions between a pair of LU 6.2-type logical units (LUs), allowing multiple operations to be performed simultaneously.  
  
 **parameter**  
 A variable used as input to a program, operating system, or API to govern how systems, programs, or functions perform.  
  
 **partitioned data set (PDS)**  
 A data set in direct access storage that is divided into partitions, called members, each of which can contain a program, part of a program, or data.  
  
 **partner**  
 An addressable component of a locality; that is, code to which messages can be sent. *See also***locality**.  
  
 **partner LU**  
 In an APPC or CPI-C conversation, the LU on the far end. The partner LU serves the partner Transaction Processor. *Contrast with***local LU**; *see also***remote LU**.  
  
 **partner LU alias**  
 A name that identifies a partner logical unit (LU) to partner transaction programs (TPs).  
  
 **partner LU name**  
 A name that identifies a partner logical unit (LU) to other LUs on the LU 6.2 session.  
  
 **partner program**  
 For CPI-C, the program receiving the CPI-C call.  
  
 **partner TPs**  
 Two transaction programs (TPs), residing on the same or separate nodes that are configured to communicate with each other. Partner TPs use partner LUs.  
  
 **password**  
 A string of characters that a user, a program, or a computer operator must specify to meet security requirements before gaining access to a system and to the information stored within it.  
  
 **path**  
 (1) In SNA, the series of nodes and communications links over which data must travel from one LU to another. (2) A sequence of folders that identify the location of a file. (3) A path exists between two localities when the DMODs in the localities can successfully pass messages between them. A path must exist between two localities before a connection can exist between partners in these localities. *See also***Dynamic Access Module (DMOD)**; **locality**.  
  
 **pattern-matching character**  
 A special character such as an asterisk (\*) or a question mark (?) that can be used to represent one or more characters. Any character or set of characters can replace a pattern-matching character. *Synonymous with* wildcard character.  
  
 **PC Support**  
 A set of IBM programs that helps personal computer users access, share, and store information on an AS/400.  
  
 **PDS**  
 *See* **partitioned data set (PDS)**.  
  
 **peer system**  
 A mainframe, midrange, or personal computer that communicates with another computer as an equal partner, with both computers sharing control over the communication.  
  
 **peer-to-peer**  
 A type of communication in which two systems communicate as equal partners sharing the processing and control of the exchange, as opposed to host-terminal communication in which the host does most of the processing and controls the exchange.  
  
 **permanent virtual circuit (PVC)**  
 A type of circuit used by an X.25 connection, in which the circuit is constantly active, and the destination address is preset.  
  
 **permissions**  
 Settings that grant or deny a particular kind of access to a particular file, folder, or other object. For example, granting read permission but denying write permission for File1.ext for Domain Admins means that the members of Admins group can read but not change File1.ext.  
  
 **physical unit (PU)**  
 A network-addressable unit that provides the services needed to use and manage a particular device, such as a communications link device. A PU is implemented with a combination of hardware, software, and microcode.  
  
 **PIC S9(4) COMP Integer**  
 A 16-bit COBOL data type that represents signed arithmetic operations occupying 2 bytes of storage. This is normally analogous to an Integer data type in Microsoft® Visual Basic® and a Short Integer in C when referring to 32-bit. It can take on values from –9999 to +9999 or –32768 to +32767. It is similar to a Short in C.  
  
 **PIC S9(9) COMP Integer**  
 A 32-bit COBOL assignment statement to represent signed arithmetic operations that occupy 4 bytes of storage. It can take on values from –999999999 to +999999999 or –2147483648 to +2147483647 depending on compiler options. It is similar to a Long Integer in C.  
  
 **PIC X**  
 Specifies a single COBOL EBCDIC character.  
  
 **PIC X No Translation**  
 A character string handled like binary data. There is no translation from EBCDIC to Unicode or from Unicode to EBCDIC.  
  
 **PICTURE clause**  
 Specifies the general characteristics and editing requirements of an elementary item. The PICTURE character string is made up of COBOL characters used as symbols and can contain a maximum of 30 characters.  
  
 **pipe**  
 A portion of memory that can be used by one process to pass information along to another.  
  
 **PLU**  
 *See* **primary logical unit (PLU)**.  
  
 **pool**  
 See LU pool.  
  
 **pooling**  
 A performance optimization based on using collections of pre-allocated resources, such as objects or database connections. Pooling results in more efficient resource allocation.  
  
 **primary logical unit (PLU)**  
 On an SNA session, the LU on the node that sent the session activation request.  
  
 **primary server**  
 The server designated to contain the primary configuration file. There can be only one primary server active in a subdomain. *See also***backup server**.  
  
 **printer emulation**  
 The ability of a personal computer-type printer to emulate a 3287 or 4224 printer to print host data.  
  
 **printer session**  
 A 3270 emulation session between a host and a local area network printer connected to a personal computer. The printer emulates the type of printer normally used by a host system.  
  
 **private assembly**  
 An assembly that is available only to clients in the same directory structure as the assembly. *See also***assembly**.  
  
 **ProgID**  
 *See* **programmatic identifier (ProgID)**.  
  
 **programmatic identifier (ProgID)**  
 A name that identifies a COM component. For example, a ProgID could be Bank.MoveMoney.  
  
 **programmatic security**  
 Procedural logic provided by a component to determine if a client is authorized to perform the requested operation. *See also***declarative security**.  
  
 **protocol**  
 (1) A set of semantic and syntactic rules that determine the behavior of functional units in achieving communication. (2) In Open Systems Interconnection architecture, a set of semantic and syntactic rules that determine the behavior of entities in the same layer in performing communication functions. (3) In SNA, the meanings of, and the sequencing rules for, requests and responses used for managing the network, transferring data, and synchronizing the states of network components.  
  
 **proxy**  
 An interface-specific object that provides the parameter marshaling and communication required for a client to call an application object that is running in a different execution environment, such as on a different thread or in another process. The proxy is located with the client and communicates with a corresponding stub that is located with the application object that is being called. In the case of TI, the TI run-time environment serves as the proxy to the mainframe transaction program (TP).  
  
 **PU**  
 *See* **physical unit (PU)**.  
  
 **PU 2.0**  
 In an SNA network, the component that defines controller and terminal-type resources similar to an IBM 3274 Control Unit.  
  
 **PU 2.1**  
 In an SNA network, a component such as an intelligent terminal or a personal computer that works together with logical unit (LU) type 6.2 to support peer-to-peer communications, allowing the LUs to function independently from the host.  
  
 **PVC**  
 *See* **permanent virtual circuit (PVC)**.  
  
## -Q-  
 **QLLC**  
 *See* **qualified logical link control (QLLC)**.  
  
 **qualified logical link control (QLLC)**  
 A protocol that permits SNA sessions to occur over X.25 networks.  
  
 **queued TP**  
 An invokable transaction program (TP) that can be started by only one incoming allocate command at a time. Incoming allocate commands that arrive while the queued TP is running do not start the program again, but are queued until the program issues another **RECEIVE_ALLOCATE** or until it finishes execution.  
  
## -R-  
 **race condition**  
 A condition in which a feedback circuit interacts with the internal circuit processes in a way that produces chaotic output behavior.  
  
 **RE**  
 *See* **remote environment (RE)**.  
  
 **Record Level Input/Output (RLIO)**  
 A protocol of IBM Distributed Data Management architecture.  
  
 **remote component**  
 Components used by a client on a different computer.  
  
 **remote environment (RE)**  
 A collection of properties that describes a region on the mainframe, or in the case of diagnostic tools such as Capture and Playback, a simulated region. You can view and change these properties by using TI Manager.  
  
 **remote LU**  
 In an APPC or CPI-C conversation, the logical unit (LU) on the remote end. *Contrast with***local LU**. *See also***remote transaction program**.  
  
 **remote network address**  
 For an 802.2 connection, a 12-digit hexadecimal address that identifies a remote host, peer, or downstream system. The Remote Network Address in Host Integration Server corresponds to the VTAM MACADDR= parameter in the PORT definition.  
  
 **remote node**  
 (1) The node at the other end of a connection. (2) The node that contains the logical unit (LU) at the other end of a session. (3) The node that contains the transaction program (TP) at the other end of a conversation.  
  
 **remote node ID**  
 One of the types of identifiers that can be used to identify a remote node. The remote node ID is an 8-digit hexadecimal number. The first three digits are called the block number, and correspond to the VTAM parameter IDBLK. The last five digits are called the node number, and correspond to the VTAM parameter IDNUM.  
  
 **remote procedure call (RPC)**  
 A standard that enables one process to make calls to functions that are executed in another process. The processes can be on the same computer or on different computers in the network.  
  
 **remote transaction program**  
 In an Advanced Program-to-Program Communications (APPC) or Common Programming Interface for Communications (CPI-C) conversation, the transaction program (TP) on the remote end. *Contrast with***local TP**. *See also***remote LU**.  
  
 **remote unit of work (RUW)**  
 (1) The form of SQL distributed processing in which the application is on a system different from the relational database, and a single application server services all remote unit-of-work requests within a single logical unit of work. (2) A unit of work that allows for the remote preparation and execution of SQL statements.  
  
 **Report Program Generator (RPG)**  
 A column-oriented programming language designed for writing application programs for business data processing. RPG requires that certain information, such as control codes and field names, must be placed into specific columns of the program statements.  
  
 **Request Unit Interface (RUI)**  
 A basic interface that enables programs to acquire and release control of conventional LUs. The RUI also reads and writes request/response headers (RHs), transmission headers (THs), and request/response unit (RU) data. *Contrast with***Session Level Interface (SLI)**.  
  
 **request/response unit (RU)**  
 Under SNA, a message that controls the session, data flow, and function management aspects of the SNA protocol.  
  
 **resource dispenser**  
 A service that helps to synchronize and manage nondurable resources within a process. This service enables efficient sharing by COM+ objects. For example, the OLE DB service components that manage pools of database connections.  
  
 **Resource Dispenser Manager**  
 A dynamic-link library (.dll) file that coordinates work among a collection of resource dispensers.  
  
 **resource manager**  
 A system service that manages durable data. Server applications use resource managers to maintain the durable state of the application, such as the record of inventory on hand, pending orders, and accounts receivable. The resource managers work in cooperation with the transaction manager to provide the application with a guarantee of atomicity and isolation (using the two-phase commit protocol). Microsoft® SQL Server™ is an example of a resource manager.  
  
 **Response Time Monitor (RTM)**  
 A 3270 and NetView facility that monitors the amount of time it takes for a host to respond during 3270 display sessions.  
  
 **RLIO**  
 *See* **Record Level Input/Output (RLIO)**.  
  
 **role**  
 A symbolic name that defines a class of users for a set of components. Each role defines which users are allowed to invoke interfaces on a component.  
  
 **root**  
 The topmost node in a directory structure.  
  
 **root directory**  
 The first directory on a drive in which all other files and subdirectories exist.  
  
 **RPC**  
 *See* **remote procedure call (RPC)**.  
  
 **RPG**  
 *See* **Report Program Generator (RPG)**.  
  
 **RTM**  
 *See* **Response Time Monitor (RTM)**.  
  
 **RU**  
 *See* **request/response unit (RU)**.  
  
 **RUW**  
 *See* **remote unit of work (RUW)**.  
  
## -S-  
 **SAA**  
 *See* **Systems Application Architecture (SAA)**.  
  
 **safe reference**  
 A reference to the current object that is safe to pass outside the context of the current object.  
  
 **SAP address**  
 *See* **service access point (SAP) address**.  
  
 **SC**  
 *See* **session control (SC)**.  
  
 **schema**  
 The definition of the structure of an XML file. A schema contains property information as it pertains to the records and fields within the structure. *See also***document type definition (DTD)**.  
  
 **SDLC**  
 *See* **Synchronous Data Link Control (SDLC)**.  
  
 **security ID (SID)**  
 A unique name that identifies a logged-on user to the security system. SIDs can identify one user or a group of users.  
  
 **security key**  
 An identifier used by two APPC logical units (LUs) to validate security when a session is activated. The security key performs a function similar to that of a password, but at the LU-LU session level rather than at the TP-conversation level.  
  
 **security log**  
 The location in which events related to security are recorded when auditing is set up for such events. For example, auditing can be set up to create a security log entry every time the configuration file is changed on a server. *See also***event log**.  
  
 **security password**  
 The password that is required, along with the security user ID, to gain access to an invoked program when using conversation security.  
  
 **security user ID**  
 The user ID (also known as user name) that is required, along with the security password, to gain access to an invoked program when using conversation security.  
  
 **semaphore**  
 A flag variable that is used to govern access to shared system resources.  
  
 **server**  
 (1) A functional unit that provides shared services to workstations over a network; for example, a file server, a print server, or a mail server. (2) In a network, a data station that provides facilities to other stations; for example, a file server, a print server, or a mail server.  
  
 **server process**  
 A process that hosts COM+ application components in Windows. For example, to use TI, you can drop a TI component (type library) into a COM+ application to create an Automation server that a client application can call. When a client application calls a method on the TI Automation server, the Windows run-time environment loads the TI Automation server along with the TI run-time environment into a surrogate server process that automates the mainframe transaction and passes the results back to the client application.  
  
 **service access point (SAP) address**  
 A value that codes for access to certain services on an 802.2 connection within an SNA network. The Remote SAP Address parameter is used for 802.2 connections in Host Integration Server, and corresponds to the VTAM parameter called SAPADDR= in the PU definition.  
  
 **service TP**  
 A transaction program (TP) that uses APPC to perform services related to SNA functionality. *See also***application TP**; **transaction program (TP)**.  
  
 **session**  
 (1) A period of time when a connection is active and communication can take place. (2) A set of resources that when activated allow communication to take place. (3) In network architecture, for the purpose of data communication between functional units, all the activities that take place during the establishment, maintenance, and release of the connection. (4) A logical connection between two network-accessible units (NAUs) that can be activated, tailored to provide various protocols, and deactivated as requested. Each session is uniquely identified in a transmission header (TH) accompanying any transmissions exchanged during the session. *See also***LU-LU session**.  
  
 **session control (SC)**  
 A subcomponent of a transmission control component of a half-session, responsible for activating and deactivating the session and data flow and for receiving the data flow following an error.  
  
 **Session Level Interface (SLI)**  
 A higher-level interface that facilitates the opening and closing of SNA sessions with host LU 0, LU 1, LU 2, and LU 3 application programs. The SLI permits application programs to control the data traffic at a logical message level. *Contrast with***Request Unit Interface (RUI)**.  
  
 **session limit**  
 The maximum number of parallel sessions that can be active between two APPC LUs. When an LU-LU session is established, the session limit is negotiated between the two LUs.  
  
 **severity level**  
 A number that indicates the severity of an audit or error message. Audit messages provide information and have severity 6, 8, or 10. Error messages have severity 12 or 16, indicating a problem that needs to be corrected.  
  
 **shared assembly**  
 An assembly that can be referenced by more than one application. An assembly must be explicitly built to be shared by giving it a cryptographically strong name. *See also***assembly**; **private assembly**.  
  
 **SID**  
 *See* **security ID (SID)**.  
  
 **side information table**  
 In CPI-C, a table that stores the initialization information required for two programs to communicate. The table resides in the operating systems memory and the system administrator maintains it by accessing a symbolic destination name. The table is derived from the configuration file for Host Integration Server.  
  
 **single session**  
 A limit of one session between a pair of Advanced Program-to-Program Communications (APPC) logical units (LUs), which limits the associated transaction programs (TPs) to one operation at a time.  
  
 **SLI**  
 *See* **Session Level Interface (SLI)**.  
  
 **SNA**  
 *See* **Systems Network Architecture (SNA)**  
  
 **SNA service TP**  
 A transaction program (TP) that uses APPC to perform services related to SNA functionality.  
  
 **SNA subdomain**  
 With SNA Server version 2.11 and SNA Server version 3.0 or later, you can have several SNA subdomains in a Windows Server domain.  
  
 A Windows Server domain:  
  
- Can contain several SNA subdomains.  
  
- Can contain several primary servers, provided that each one is set up in its own subdomain.  
  
  With regard to Host Integration Server, each subdomain:  
  
- Contains one primary server.  
  
- Can contain up to 14 backup servers.  
  
- Cannot contain computers running Host Integration Server from other Windows Server domains.  
  
  Host Integration Server Setup requires you to specify the name of the subdomain to which the server will belong. One of the SNA subdomains can have the same name as that of the Windows Server domain in which all the servers operate.  
  
  Because each subdomain can have only one primary server, it is not advisable to implement an SNA subdomain across slow bridges or routers. Multiple servers in a single subdomain can produce unwanted traffic on the wide-area network.  
  
  **SnaBase**  
  The SNA Workstation Process. It is present at all times on personal computers whose users want to participate in the SNA network and on personal computers where dynamic loading is to be performed.  
  
  **SNALink**  
  Link support software that integrates hardware components into a Host Integration Server system. An SNALink is defined when a Host Integration Server system is installed. An SNALink can support only one physical connection from the server.  
  
  **source TP Name**  
  The host system attempts to identify the source of a request for monitoring, reporting, and so on. The source must be a TP name. MSTX is the default, because it is usually a Component Services process.  
  
  **SSCP**  
  *See* **system services control point (SSCP)**.  
  
  **string expression**  
  Any expression that evaluates to a sequence of contiguous characters.  
  
  **stub**  
  An interface-specific object that provides the parameter marshaling and communication required for an application object to receive calls from a client that is running in a different execution environment, such as on a different thread or in another process. The stub is located with the application object and communicates with a corresponding proxy that is located with the client that calls it. In the case of TI, the TI run-time environment serves as the proxy.  
  
  **subdirectory**  
  A directory contained within another directory in a file system hierarchy.  
  
  **subdomain**  
  A collection of computers running Host Integration Server that share a single configuration. A subdomain contains one primary server and can also contain one or more backup servers. All servers in a subdomain must belong to the same Windows domain. *See also***backup server**; **primary server**.  
  
  **SVC**  
  *See* **switched virtual circuit (SVC)**.  
  
  **switched SDLC line**  
  A standard telephone line used for SDLC connections on an SNA network. The line is dialed in one of three ways: manually, by a modem that stores the phone number, or by a modem that accepts a phone number string from the software.  
  
  **switched virtual circuit (SVC)**  
  A type of circuit used by an X.25 connection, in which the circuit is not constantly active, but is called and cleared dynamically. The destination address is supplied when the circuit is called.  
  
  **Synchronous Data Link Control (SDLC)**  
  A type of link service used for managing synchronous data transfer over standard telephone lines (switched lines) or leased lines.  
  
  **synchronous transmission**  
  Transmission in which the data characters and bits are transmitted at a fixed rate, with the transmitter and receiver being synchronized. This eliminates the need for individual start and stop bits surrounding each byte. Both SDLC and X.25 use synchronous transmission.  
  
  **synchronous verb completion**  
  Processing of an SNA verb where the operation of the program is blocked until processing completes. *Contrast with***asynchronous verb completion**.  
  
  **system administrator**  
  A person who configures, maintains the configuration of, helps users diagnose problems with, and manages a computer system. With Host Integration Server, this person can also be the LAN administrator or a TI developer.  
  
  **system services control point (SSCP)**  
  (1) A host system network component that provides network services for dependent nodes. (2) An SNA network component that helps control and maintain communication flow between PUs and LUs on the network. Multiple SSCPs can work together to coordinate communications.  
  
  **Systems Application Architecture (SAA)**  
  Guidelines created by IBM to help developers standardize applications so they function in different operating environments with minimal program modification and retraining of users.  
  
  **Systems Network Architecture (SNA)**  
  The description of the logical structure, formats, protocols, and operational sequences for transmitting information units through, and controlling the configuration and operation of, networks  
  
## -T-  
 **TCP/IP**  
 *See* **Transmission Control Protocol/Internet Protocol (TCP/IP)**.  
  
 **terminal**  
 A device that can send or receive data over a data communications channel. Host Integration Server includes emulation of 3278 and 3279 terminals.  
  
 **TH**  
 *See* **transmission header (TH)**.  
  
 **thread**  
 The basic entity to which the operating system allocates CPU time. A thread can execute any part of the application's code, including a part currently being executed by another thread. All threads of a process share the virtual address space, global variables, and operating system resources of the process.  
  
 **TI**  
 *See* **Transaction Integrator (TI)**.  
  
 **Token Ring**  
 A type of LAN using the 802.2 protocol, in which a token is passed in a ring around the network, permitting a computer on the network to transmit data only when that computer has the token.  
  
 **TP**  
 *See* **transaction program (TP)**.  
  
 **trace file**  
 A file containing records of internal activities on the SNA network, including calls made to APIs, the activities of APIs, and the activities of communication links and internal flows.  
  
 **trace message**  
 A message that includes the current status of various COM+ activities, such as startup and shutdown.  
  
 **tracing**  
 The action of tracking the activities of an application programming interface (API), communication links, and internal flows, including the calls made to APIs. Tracing stores a history of activity in trace files.  
  
 **transaction**  
 Data entered into a system (such as a customer deposit to a bank account) triggering a certain action (such as updating an account balance).  
  
 An atomic unit of work in COM-based systems that either succeeds or fails as a whole or a section of a mainframe COBOL transaction program (TP). A mainframe-based transaction is a section of COBOL code within a transaction program (TP) that completes a certain task or set of tasks.  
  
 A mainframe transaction may or may not be an ACID (atomic, consistent, isolated, and durable) transaction. A mainframe-based TP is the actual COBOL program file that contains one or more transactions (sections of COBOL code). A Windows-based transaction is always an ACID transaction that is coordinated by the Microsoft Distributed Transaction Coordinator (DTC).  
  
 Data entered into a system (such as a customer deposit to a bank account) triggers a certain action or set of actions (such as updating an account balance) that must all occur or that must all not occur; that is, they act as a unit. That unit is called a transaction in Windows-based terminology.  
  
 Each method in a TI component invokes a single mainframe transaction in a mainframe TP. After being invoked, a mainframe transaction can call other transactions in the same or in a different TP.  
  
 **transaction context**  
 An object used to allow a client to dynamically include one or more objects in one transaction.  
  
 **transaction ID**  
 The identifier used to invoke a particular CICS or IMS application (transaction program); in CICS, it is the name of the transaction. A transaction ID (TRANID) can be up to four characters in length. The acceptable characters are A-Z, a-z, 0-9, dollar sign ($), at sign (@), period (.), slash mark (/), hyphen (-), underscore (_), percent sign (%), ampersand (&), question mark (?), exclamation point (!), colon (:), vertical bar (&#124;), quotation mark ("), equal sign (=), caret (^), comma (,), semicolon (;), less than sign (\<), and greater than sign (>).  
  
 **Transaction Integrator (TI)**  
 A Windows server-based program that enables you to integrate mainframe or midrange computer transaction programs with component-based and .NET Framework applications.  
  
 **transaction manager**  
 The transaction manager creates transaction objects and manages their atomicity and durability. Applications request the creation of a transaction object by calling the transaction manager's **BeginTransaction** method.  
  
 **transaction program (TP)**  
 A COBOL-based mainframe transaction program file. An application program that uses Advanced Program-to-Program Communications (APPC) to exchange data with another TP on a peer-to-peer basis. Within the context of TI, a TP is the mainframe-based CICS or IMS program file that a TI Automation server automates. A TP can contain one or more transactions that are managed on the mainframe side. Each method in a single TI Automation server invokes a single TP. That TP then uses the information passed into it by the TI Automation server to determine which mainframe transaction to run within the TP. Each mainframe transaction within a TP can call other transactions. It is dependent upon how the mainframe COBOL application developer has designed the system.  
  
 (1) An application program that uses APPC or CPI-C to exchange data with another TP on a peer-to-peer basis. (2) A program that processes transactions in an SNA network. There are two kinds of transaction programs: application transaction programs and service transaction programs. *See also* **conversation**.  
  
 **Transmission Control Protocol/Internet Protocol (TCP/IP)**  
 The transport protocol in use by many academic, military, scientific, and commercial organizations to provide communication across wide area networks (WANs). TCP/IP provides communication across interconnected networks that include a variety of different operating systems (such as VMS, UNIX, and Windows).  
  
 **transmission header (TH)**  
 A header prefix to a message unit flowing within the Path Control Network (PCN), and containing PCN-specific data about routing, sequencing, blocking, and route pacing.  
  
 **Twinax**  
 A twinaxial connection to a peer system.  
  
 **twisted-pair cable**  
 Two paired wires, with each wire twisted two or more times per inch to help cancel out noise.  
  
 **two-phase commit (2PC)**  
 A protocol that ensures that transactions that apply to more than one server are completed on all the servers or none at all. Two-phase commit is coordinated by the transaction manager and supported by resource managers.  
  
 **type library**  
 A file (or component within another file) that contains Automation descriptions of exposed objects, properties, and methods. Object library (.olb) files contain type libraries. Type libraries that are shipped as stand-alone files use the file extension .tlb. A TI component is an example of a type library (.tlb file).  
  
## -U-  
 **UDA**  
 *See* **universal data access (UDA)**.  
  
 **UDT**  
 *See* **user-defined type (UDT)**.  
  
 **unbounded**  
 Refers to recordsets or arrays. In TI, the rows in a recordset or the elements in an array are transmitted one at a time. Therefore, the mainframe application program must issue multiple receives or sends until all data is transmitted.  
  
 This type of parameter or return value can be defined as unbounded for the **CICS Using LU 6.2** and **IMS Using LU 6.2** models only. The number of rows in a recordset or the number of elements in an array is not determined (that is, bounded) before run time. Unbounded parameters or return values can occur anywhere in the Automation method. However, a parameter or return value of this type is always transmitted to and from the mainframe after all other data. TI supports, at most, a single unbounded input parameter and a single unbounded output parameter or a single unbounded in/out parameter.  
  
 **universal data access (UDA)**  
 A Microsoft data access method which supplies access to information across the enterprise. Universal data access provides high-performance access to a variety of information sources, including relational and non-relational, and an easy to use programming interface that is tool and language independent.  
  
 **user alert**  
 A message sent by a 3270 user to a host system operator by way of NetView, requesting an action such as mounting a tape or changing forms on a printer.  
  
 **user identifier**  
 A string of characters that uniquely identifies a user to a system.  
  
 **user name**  
 The name (also known as user ID) that identifies a Windows user account.  
  
 **user-defined type (UDT)**  
 A data type that is defined in a program. User-defined data types generally contain many different data types that are defined by the programming language being used. In COBOL, UDTs are called RECORDS (that is, any declaration containing lower-level numbers).  
  
## -V-  
 **variable-length string**  
 A fundamental data type that holds character information. A String variable can contain approximately 65,535 bytes (64 KB), and it is either fixed-length or variable-length. Strings usually have one character per byte; however, TI supports Unicode BSTR strings that occupy 16 bits per character. Fixed-length strings are declared to be a specific length, and variable-length strings can be any length up to 64 KB, less a small amount of storage overhead.  
  
 **VCB**  
 *See* **verb control block (VCB)**.  
  
 **verb**  
 Command from one LU to another to exchange data and perform tasks. *See also***APPC verb**.  
  
 **verb control block (VCB)**  
 A structure made up of variables, which identifies the verb to be executed, supplies information to be used by the verb, and contains information returned by the verb when execution is complete.  
  
 **VINES**  
 *See* **VIrtual NEtworking System (VINES)**.  
  
 **VIrtual NEtworking System (VINES)**  
 A collection of networking software products from Banyan Systems, Inc. VINES includes an addressing system called StreetTalk.  
  
 **Virtual Telecommunications Access Method (VTAM)**  
 A set of IBM mainframe programs that control communications between mainframe applications and the terminals and computers that connect to the mainframe.  
  
 **VTAM**  
 *See* **Virtual Telecommunications Access Method (VTAM)**.  
  
## -W-  
 **WAN**  
 *See* **wide area network (WAN)**.  
  
 **wide area network (WAN)**  
 A high-speed communication system, consisting of hardware (computers and peripherals) and software (programs and files), that provides communications services and enables resources to be shared over a larger geographic area than that served by a LAN. *Contrast with***local area network (LAN)**.  
  
 **wildcard character**  
 *Synonym for* pattern-matching character.  
  
 **Windows-initiated processing (WIP)**  
 A Windows server platform can access and integrate its programs with the programs on a non-Microsoft server platform (usually a mainframe or mid-range computer such as the AS/400).  
  
 **WIP**  
 *See* **Windows-initiated processing (WIP)**.  
  
## -X-  
 **X.25**  
 The CCITT standard used for communication over a packet-switching network. X.25 uses the protocol called qualified logical link control (QLLC).  
  
 **XID**  
 *See* **exchange identification (XID)**.  
  
 **XML**  
 *See* **Extensible Markup Language (XML)**.  
  
 **XML Schema Definition (XSD)**  
 A language proposed by the W3C XML Schema Working Group for use in defining schemas. Schemas are useful for enforcing structure and constraining the types of data that can be used validly within other XML documents. Unlike DTD, which requires its own language and syntax, XSD uses XML syntax for its language. XSD closely resembles and extends the capabilities of XDR. The W3C now recommends the use of XSD as a standard for defining XML schemas.  
  
 **XSD**  
 *See* **XML Schema Definition (XSD)**.  
  
 **XSL**  
 *See* **Extensible Stylesheet Language (XSL)**.  
  
## -Y-  
 No terms.  
  
## -Z-  
 No terms.  
  
## See Also  
 [Application Integration (Planning)](../core/application-integration-planning-2.md)