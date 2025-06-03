---
title: Choosing the Appropriate Programming Model
description: Learn more about choosing the appropriate programming model for your solution.
ms.service: host-integration-server
ms.topic: concept-article
ms.date: 11/30/2017
---

# Choosing the appropriate programming model for your solution

A programming model determines the method used to access and integrate host applications and configuration requirements depending on the specific solution goals. If you implement TI or use the connectors for mainframe and midrange systems to create workflows in Azure Logic Apps, you might have to change the existing mainframe transaction programs (TPs) to fit the programming models that they support. Specifically, this might be necessary when in these scenarios:
  
- A TP doesn't expect a simple request-reply response.
  
- A CICS TP has terminal processing logic embedded in the same TP with the business logic.

  You must restructure this type of TP as two separate TPs. Access to business logic that already exists on the mainframe computer as TPs. You can use this function, or you can create the methods on the COM side and then create the necessary server TPs on the mainframe computer. This is still a viable option because TI might be better for accessing some types of data, such as those stored in VSAM data sets, than standard data access methods.  
  
  You must carefully analyze your organization's business requirements so that you can implement transaction access by using one of the programming models provided in TI. TI supports the programming models listed in the following table, which lists some of the factors that you should consider when you choose the appropriate programming model for your organization:

  - The network protocol
  - The maximum size of the message or data that can be sent to the host
  - Whether you need to use two-phase commit transactions in host applications
  - Whether you have to write your own communications protocol to support a Link program
  - Whether you want the server to have the ability to maintain the client to server context, also referred to as a persistent connection
  - Other requirements specific to a particular model

The following table summarizes the similarities and differences across the programming models:

| Programming model | Network protocol | Maximum message or data size | Supports two-phase commit | Write own communications protocol | Supports persistent connections | Supports Azure Logic Apps | Other requirements |
|-------------------|------------------|------------------------------|---------------------------|-----------------------------------|---------------------------------|---------------------------|--------------------|
| [TCP Transaction Request Message Link](tcp-transaction-request-message-link2.md) | TCP/IP | 32 KB | No | No (see sample code) | Yes | Yes | - See mscmtics.cbl sample application. <br>- 1:many relationship between server application and port |
| [TCP Enhanced Listener Message Link](tcp-enhanced-listener-message-link1.md) |TCP/IP | 32 KB | No | No (see sample code) | Yes | Yes | - See mscmtics.cbl sample application. <br>- 1:1 relationship between server application and port |
| [TCP Transaction Request Message User Data](tcp-transaction-request-message-user-data2.md) | TCP/IP | Unlimited | No | Yes <br><br>(Server TPs are coded to handle all socket calls over TCP/IP.) | Yes | Yes | 1:many relationship between server application and port |
| [TCP Enhanced Listener Message User Data](tcp-enhanced-listener-message-user-data2.md)| TCP/IP | Unlimited | No | Yes <br><br>(Server TPs are coded to handle all socket calls over TCP/IP.) | Yes | Yes | 1:1 relationship between server application and port |
| [IMS Connect](ims-connect1.md) | TCP/IP | 10MB | No | No | No | Yes | - No inbound (from TI to the host) unbounded recordsets are allowed. TI can't send unbounded recordsets to the host. Only recordsets coming back from the host to TI are supported. <br>- Dependent on the IBM supplied HWSIMSO0 and HWSIMSO0 exit routines |
| [IBM i Distributed Program Calls](os-400-distributed-program-calls1.md) | TCP/IP | 32KB | No | No | Yes | No | |
| [CICS LU6.2 Link](../core/cics-lu6-2-link1.md)| LU6.2 | 32KB | Yes | No | No | No | - Server TPs are already coded to use the COMMAREA. **Note**: CICS Link doesn't support multiple send-and-receive commands. So, variable length recordsets aren't supported, but fixed-sized recordsets are supported. <br>- CICS TPs don't contain the necessary logic to handle issuing APPC verbs directly, but instead must rely on the CICS Mirror transaction. <br>- The TP is coded for a simple send-and-receive sequence. |
| [CICS LU6.2 User Data](../core/cics-lu6-2-user-data2.md) | LU6.2 | Unlimited | Yes | Yes <br><br>(Server TPs are coded to handle all APPC and Sync Level 2 communications.) | Yes | No | - Existing TPs contain the proper code necessary to manage their own APPC and Sync Level 2 communications. <br>- Can use multiple send-and-receive commands. |
| [IMS LU6.2 User Data](../core/ims-lu6-2-user-data1.md)| LU6.2 | Unlimited | Yes | No | No | No | - Each server TP must have the embedded code necessary to handle all data communications using the LU6.2 protocol. |
| **HTTP Link** | HTTP | 32 KB | No | No | No (see sample code) | Yes | - See MSHMIRS sample programs <br>- 1:many relationship between server application and port |
| **HTTP User Data** | HTTP | Unlimited | No | No | Yes, based on sample code in HTTPGetBalanceUserData.cbl | Yes | - See GETBALUD sample program <br>- 1:many relationship between server application and port |
  
If you implement a specific programming model, you must install and configure the appropriate software on your mainframe or IBM i computer. When you choose the appropriate programming model for your organization, you might want assess how closely your current host configuration matches the minimum requirements. The following table summarizes the minimum software and configuration requirements for each programming model:

| Programming model | Requirement to install and configure |
|-------------------|--------------------------------------|
| [TCP Transaction Request Message Link](tcp-transaction-request-message-link2.md) | - IBM z/OS 2.3 or later <br>- IBM CICS 5.2 or later <br>- The Listener TP, which is included in CICS TCP/IP, configured and started <br>- TCP/IP for z/OS version 2.3 or later <br> - At least one CICS region defined in an APPL statement in VTAM with TPs configured. |
| [TCP Enhanced Listener Message Link](tcp-enhanced-listener-message-link1.md) | - IBM z/OS 2.3 or later <br>- IBM CICS Component Services <br>- The Listener TP, which is included in CICS TCP/IP, configured and started <br>- TCP/IP for z/OS version 2.3 or later <br>- At least one CICS region defined in an APPL statement in VTAM with TPs configured |
| [TCP Transaction Request Message User Data](tcp-transaction-request-message-user-data2.md)| - IBM z/OS 2.3 or later <br>- IBM CICS 5.2 or later <br>- The Listener TP, which is included in CICS TCP/IP, configured and started <br>- TCP/IP for z/OS version 2.3 or later <br>- At least one CICS region defined in an APPL statement in VTAM with TPs configured |
| [TCP Enhanced Listener Message User Data](tcp-enhanced-listener-message-user-data2.md) | - IBM z/OS 2.3 or later <br>- IBM CICS Component Services <br>- The Listener TP, which is included in CICS TCP/IP, configured and started <br>- TCP/IP for z/OS  version 2.3 or later <br>- At least one CICS region defined in an APPL statement in VTAM with TPs configured |
| [IMS Connect](ims-connect1.md)| - IBM z/OS 2.3 or later <br>- IBM IMS 13.1 or later <br>- The Listener TP included in IMS TCP/IP <br>- TCP/IP for z/OS 2.3 or later <br>- IMS TCP/IP |
| [IBM i Distributed Program Calls](os-400-distributed-program-calls1.md)| IBM IBM i release 4 version 1 or later |
| [CICS LU6.2 Link](cics-lu6-2-link1.md) | - IBM z/OS 2.3 or later <br>- IBM CICS version 5.2 or later <br>- The CICS Mirror transaction, which is included in CICS version 5.2 or later <br>- VTAM <br>- At least one CICS region defined in an Application (APPL) statement in VTAM with TPs configured <br>- The proper VTAM PU, LU, and Mode definitions necessary to establish Systems Network Architecture (SNA) connectivity |
| [CICS LU6.2 User Data](cics-lu6-2-user-data2.md) | - IBM z/OS 2.3 or later <br>- IBM CICS 5.2 or later <br>- VTAM <br>- At least one CICS region defined in an APPL statement in VTAM with TPs configured <br>- The proper VTAM PU, LU, and Mode definitions necessary to establish SNA connectivity |
| [IMS LU6.2 User Data](../core/ims-lu6-2-user-data1.md)| - IBM z/OS 2.3 or later <br>- MVS/APPC must be installed on the mainframe computer. MVS/APPC is included with the operating system. <br>- IBM IMS 13.1 or later <br>- IBM IMS 13.1 or later if using 2PC protocols (Sync Point level 2) <br>- IBM Recovery Resource Services (RRS) if using 2PC protocols (Sync Point level 2). In addition, the proper IMS control regions must be defined in an APPL statement in VTAM. |

## See also

[Programming Models](../core/programming-models2.md)   
[Two-Phase Commit](../core/two-phase-commit2.md)
