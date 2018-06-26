---
title: "Choosing the Appropriate Programming Model1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 803bb2c1-38fe-4963-a2ca-70531f43725d
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Choosing the Appropriate Programming Model
A TI programming model determines the method used to access and integrate host applications and TI configuration requirements depending on the specific TI programming model being used. Implementing TI may require modification to the existing mainframe TPs to be able to fit the programming models that it supports. Specifically, this may be necessary when:  
  
- A TP does not expect a simple request-reply response.  
  
- A CICS TP has terminal processing logic embedded in the same TP with the business logic. This type of TP must be restructured as two separate TPs. Accesses business logic that already exists on the mainframe computer as TPs. You can use this function, or you can create the methods on the COM side and then create the necessary server TPs on the mainframe computer. This is still a viable option because TI may be better for accessing some types of data, such as those stored in VSAM data sets, than standard data access methods.  
  
  You must carefully analyze the business requirements of your organization so that you can implement transaction access by using one of the programming models provided in TI.  
  
  TI supports the programming models listed in the table below. Some of the factors you should consider when choosing the appropriate programming model for your organization are:  
  
- the network procotol  
  
- the maximum size of the message or data that can be sent to the host  
  
- whether you need to use two-phase commit transactions in host applications  
  
- whether you have to write your own communications protocol to support a Link program  
  
- whether you want the server to have the ability to maintain the client to server context, also referred to as a persistent connection  
  
- other requirements specific to a particular model.  
  
  The following table summarizes the similarities and differences among the programming models.  
  
|Programming Model|Network Protocol|Maximum Message or Data Size|Supports Two-phase Commit?|Write Own Communi-cations Protocol?|Supports Persistent Connect-ions?|Other Requirements|  
|-----------------------|----------------------|----------------------------------|---------------------------------|------------------------------------------|----------------------------------------|------------------------|  
|[TCP Transaction Request Message Link](../core/tcp-transaction-request-message-link2.md)|TCP/IP|32 KB|No|No (see sample code)|Yes|-   See mscmtics.cbl sample application.<br />-   1:many relationship between server application and port.|  
|[TCP Enhanced Listener Message Link](../core/tcp-enhanced-listener-message-link1.md)|TCP/IP|32 KB|No|No (see sample code)|Yes|-   See mscmtics.cbl sample application.<br />-   1:1 relationship between server application and port.|  
|[TCP Transaction Request Message User Data](../core/tcp-transaction-request-message-user-data2.md)|TCP/IP|unlimited|No|Yes<br /><br /> (Server TPs are coded to handle all socket calls over TCP/IP)|Yes|-   1:many relationship between server application and port.|  
|[TCP Enhanced Listener Message User Data](../core/tcp-enhanced-listener-message-user-data2.md)|TCP/IP|unlimited|No|Yes<br /><br /> (Server TPs are coded to handle all socket calls over TCP/IP)|Yes|-   1:1 relationship between server application and port.|  
|[IMS Connect](../core/ims-connect1.md)|TCP/IP|10MB|No|No|No|-   No inbound (from TI to the host) unbounded recordsets are allowed. TI cannot send unbounded recordsets to the host; only those recordsets coming back from the host to TI are supported.<br />-   Dependent on the IBM supplied HWSIMSO0  and HWSIMSO0 exit routines.|  
|[OS/400 Distributed Program Calls](../core/os-400-distributed-program-calls1.md)|TCP/IP|32KB|No|No|Yes||  
|[CICS LU6.2 Link](../core/cics-lu6-2-link1.md)|LU6.2|32KB|Yes|No|No|-   Server TPs are already coded to use the COMMAREA. **Note:**      CICS Link does not support multiple send-and-receive commands. Therefore, variable length recordsets are not supported, but fixed-sized recordsets are supported.<br />-   CICS TPs do not contain the necessary logic to handle issuing APPC verbs directly, but instead must rely on the CICS Mirror transaction.<br />-   The TP is coded for a simple send-and-receive sequence.|  
|[CICS LU6.2 User Data](../core/cics-lu6-2-user-data2.md)|LU6.2|unlimited|Yes|Yes<br /><br /> (Server TPs are coded to handle all APPC and Sync Level 2  communica-tions.)|Yes|-   Existing TPs contain the proper code necessary to manage their own APPC and Sync Level 2 communications.<br />-   Can use multiple send-and-receive commands.|  
|[IMS LU6.2 User Data](../core/ims-lu6-2-user-data1.md)|LU6.2|unlimited|Yes|No|No|-   Each server TP must have the embedded code necessary to handle all data communications using the LU6.2 protocol.|  
|**HTTP Link**|HTTP|32 KB|No|No|No (see sample code)|-   See MSHMIRS sample Programs<br /><br /> -   1:many relationship between server application and port.|  
|**HTTP User Data**|HTTP|unlimited|No|No|Yes (based on sample code in HTTPGetBalanceUserData.cbl)|-   See GETBALUD sample Program<br /><br /> -   1:many relationship between server application and port.|  
  
||||||||  
|-|-|-|-|-|-|-|  
|**HTTP Link**|HTTP|32 KB|No|No|No (see sample code)|-   See MSHMIRS sample Programs<br /><br /> -   1:many relationship between server application and port.|  
|**HTTP User Data**|HTTP|unlimited|No|No|Yes (based on sample code in HTTPGetBalanceUserData.cbl)|-   See GETBALUD sample Program<br /><br /> -   1:many relationship between server application and port.|  
  
 Implementing a specific programming model requires that you install and configure the appropriate software on your mainframe or AS/400 computer. When choosing the appropriate programming model for your organization, you might want assess how closely your current host configuration match the minimum requirements. The following table summarizes the minimum software and configuration requirements for each programming model.  
  
|Programming Model|To use this model, you must install and configure|  
|-----------------------|-------------------------------------------------------|  
|[TCP Transaction Request Message Link](../core/tcp-transaction-request-message-link2.md)|-   IBM MVS operating system 4.3 or later.<br />-   IBM CICS 4.0 or later.<br />-   The Listener TP, which is included in CICS TCP/IP, configured and started.<br />-   TCP/IP for MVS version 3.2 or later.<br />-   At least one CICS region defined in an APPL statement in VTAM with TPs configured.|  
|[TCP Enhanced Listener Message Link](../core/tcp-enhanced-listener-message-link1.md)|-   IBM MVS operating system 4.3 or later.<br />-   IBM CICS Component Services.<br />-   The Listener TP, which is included in CICS TCP/IP, configured and started.<br />-   TCP/IP for MVS version 3.2 or later.<br />-   At least one CICS region defined in an APPL statement in VTAM with TPs configured.|  
|[TCP Transaction Request Message User Data](../core/tcp-transaction-request-message-user-data2.md)|-   IBM MVS operating system 4.3 or later.<br />-   IBM CICS 4.0 or later.<br />-   The Listener TP, which is included in CICS TCP/IP, configured and started.<br />-   TCP/IP for MVS version 3.2 or later.<br />-   At least one CICS region defined in an APPL statement in VTAM with TPs configured.|  
|[TCP Enhanced Listener Message User Data](../core/tcp-enhanced-listener-message-user-data2.md)|-   IBM MVS operating system 4.3 or later.<br />-   IBM CICS Component Services.<br />-   The Listener TP, which is included in CICS TCP/IP, configured and started.<br />-   TCP/IP for MVS version 3.2 or later.<br />-   At least one CICS region defined in an APPL statement in VTAM with TPs configured.|  
|[IMS Connect](../core/ims-connect1.md)|-   IBM MVS operating system 4.3 or later.<br />-   IBM IMS 4.1 or later.<br />-   The Listener TP included in IMS TCP/IP.<br />-   TCP/IP for MVS version 3.2 or later.<br />-   IMS TCP/IP.|  
|[OS/400 Distributed Program Calls](../core/os-400-distributed-program-calls1.md)|-   IBM OS/400 release 4 version 1 or later.|  
|[CICS LU6.2 Link](../core/cics-lu6-2-link1.md)|-   IBM MVS operating system version 4.3 or later.<br />-   IBM CICS version 3.3 or later.<br />-   The CICS Mirror transaction, which is included in CICS version 3.3 or later.<br />-   VTAM.<br />-   At least one CICS region defined in an Application (APPL) statement in VTAM with TPs configured.<br />-   The proper VTAM PU, LU, and Mode definitions necessary to establish Systems Network Architecture (SNA) connectivity|  
|[CICS LU6.2 User Data](../core/cics-lu6-2-user-data2.md)|-   IBM MVS operating system 4.3 or later, including OS/390.<br />-   IBM CICS 3.3 or later.<br />-   VTAM.<br />-   At least one CICS region defined in an APPL statement in VTAM with TPs configured.<br />-   The proper VTAM PU, LU, and Mode definitions necessary to establish SNA connectivity.|  
|[IMS LU6.2 User Data](../core/ims-lu6-2-user-data1.md)|-   IBM MVS operating system 4.3 or later.<br />-   MVS/APPC must be installed on the mainframe computer. MVS/APPC is included with the operating system.<br />-   IBM IMS 4.0 or later.<br />-   IBM IMS 6.0 or later if using 2PC protocols (Sync Point level 2).<br />-   IBM Recovery Resource Services (RRS) if using 2PC protocols (Sync Point level 2). In addition, the proper IMS control regions must be defined in an APPL statement in VTAM.|  
  
## See Also  
 [Programming Models](../core/programming-models2.md)   
 [Two-Phase Commit](../core/two-phase-commit2.md)