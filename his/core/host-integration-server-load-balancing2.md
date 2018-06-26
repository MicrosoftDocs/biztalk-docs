---
title: "Host Integration Server Load Balancing2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21928503-d481-4c42-9eae-b0135febafe1
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Host Integration Server Load Balancing
Transaction Integrator (TI) can use [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] load balancing and hot backup capability by deploying multiple [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] End-User Client and [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Server computers in a single subdomain. Redundant APPC session pairs can be configured across multiple Host Integration Server computers to provide load balancing and hot backup. When a communication failure occurs, hot backup reroutes sessions to other host connections. For information about how to set up a hot backup system for two-phase commit and TI, see [Providing a Fail-Safe Environment for ACID Transactions](./providing-a-fail-safe-environment-for-acid-transactions1.md).  
  
## Autoactivating Sessions  
 For sessions to be spread across several servers, you must configure the mode definition to autoactivate sessions. When an APPC application (such as TI) requests a conversation, the APPC library sends a non-forced open LU 6.2 request to every node (SNA Server), which has the required Local logical unit (LU) (or a Local LU in the default pool if no LU name is specified). The node returns an error that indicates the best connection to use. The APPC library then chooses the response that has the lowest error number and issues a forced open LU 6.2 request.  
  
### LU 6.2 Errors  
 The errors for LU 6.2 are as follows:  
  
 0804 = Connection is disabled.  
  
 0604 = Session limits reached for LU/LU/mode.  
  
 0404 = Dependent LU - Connection active, but no LU-SSCP session active.  
  
 0204 = Dependent LU - LU-SSCP active, and PLU-SLU session already in-use.  
  
 0008 = Connection is pending.  
  
 0004 = Connection is inactive, no LU-SSCP session active.  
  
 0003 = If dependent LU, no LU-SSCP or PLU-SLU session active. If independent LU, CNOS not done yet for this LU/LU/mode.  
  
 0002 = Independent LU - CNOS done but no sessions currently active.  
  
 If the connection has an active session available (in other words, it is a bound session without a conversation established), the non-forced open LU 6.2 is processed by the node and returns a positive response to the APPC library (assuming it was successful in its request to the host).  
  
 For load balancing to work correctly, all connections must have active sessions available. If this is not the case, the first connection to establish a conversation is always chosen by the APPC library because it will return a lower error than the other connections. You can configure connections to autoactivate sessions by setting the autoactivation limit and LU partnering in the mode definition.  
  
## Configuring TI and Host Integration Server for Load Balancing  
 TI must also be installed on its own server independent of the two Host Integration Servers that have connections to the host. If TI is installed on either of the two servers that have connections to the host, load balancing will not function.  
  
 The Host Integration Server client process (the SnaBase service on Windows) opens a sponsor connection to the SnaBase service on a Host Integration Server computer in the subdomain. This sponsor connection remains active while the Host Integration Server client process is running. When the Host Integration Server client process first starts, the client receives a list of all Host Integration Server computers in the subdomain. After that, only server changes are sent.  
  
### Host Integration Server  
 To configure Host Integration Server for APPC Load Balancing, define redundant local LU and remote LU aliases across Host Integration Server computers by using SNA Manager. For example:  
  
 **Server 1**  
  
- Local APPC LU alias=COMTI  
  
- Local APPC LU network name=APPN and LU name=SERVER1  
  
- Select the **Member of default outgoing Local APPC LU pool** check box  
  
- Remote APPC LU alias=CICS  
  
- Remote APPC LU network name=APPN and LU name=CICS  
  
  **Server**  
  
- Local APPC LU alias=COMTI  
  
- Local APPC LU network name=APPN and LU name=SERVER2  
  
- Select the **Member of default outgoing Local APPC LU pool** check box  
  
- Remote APPC LU alias=CICS  
  
- Remote APPC LU network name=APPN and LU name=CICS  
  
  **Server**  
  
- Local APPC LU alias=COMTI  
  
- Local APPC LU network name=APPN and LU name=SERVER3  
  
- Select the **Member of default outgoing Local APPC LU pool** check box  
  
- Remote APPC LU alias=CICS  
  
- Remote APPC LU network name=APPN and LU name=CICS  
  
#### Required Parameters  
 The following table references the required Host Integration Server, VTAM, and CICS parameters.  
  
|Host Integration Server|VTAM|CICS|  
|-----------------------------|----------|----------|  
|Local Node ID—First 3 Digits|IDBLK in PU definition|Not applicable|  
|Local Node ID—Last 5 Digits|IDNUM in PU definition|Not applicable|  
|Control Point Name|CPNAME in PU definition|Not applicable|  
|Max BTU Length|MAXDATA in the PU|Not applicable|  
|Local APPC LU Name|Name in LU definition|Sessions|  
|APPC Mode|DLOGMOD in the LU definition|Mode name|  
|Remote APPC LU Name|Not applicable|APPLID|  
  
### Transaction Integrator  
 To configure TI to use the Host Integration Server load balancing capability, you must do the following:  
  
-   Configure the "CICS Link using LU 6.2," "CICS using LU 6.2," or "IMS using LU 6.2" remote environments for the same local LU alias and remote LU alias defined on the Host Integration Server computer.  
  
-   Create a unique Local Node ID on each Host Integration Server computer, configured for hot backup to occur across Host Integration Server computers to a single host. (LOCADDR in the VTAM definition must be set to 0 to support independent LU 6.2.)  
  
-   Define the following registry entry on the Host Integration Server End-user client:  
  
     **KEY_LOCAL_MACHINE\System\CurrentControlSet\Services\SnaBase\Parameters\Client\ ResLocFlags: REG_DWORD: 0x8001**  
  
-   In mode definition, set the autoactivation limit and LU partnering limits. This configures your connections to autoactivate sessions.  
  
## See Also  
 [Load Balancing and Hot Backup](../core/load-balancing-and-hot-backup2.md)   
 [Transaction Integrator User's Guide](../core/transaction-integrator-user-s-guide2.md)