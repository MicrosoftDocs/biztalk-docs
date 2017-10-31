---
title: "WMISNA WMI Provider Classes2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42525c3e-64a6-432b-8e93-b8d44c3f7c3b
caps.latest.revision: 3
---
# WMISNA WMI Provider Classes
The Microsoft Host Integration Server SNA configuration provider supplies information regarding the SNA service configuration. As an instance and method provider, the WMISNA provider implements the standard **IWbemProviderInit** interface and the following **IWbemServices** methods:  
  
-   **CreateInstanceEnumAsync**  
  
-   **DeleteInstanceAsync**  
  
-   **ExecMethodAsync**  
  
-   **ExecQueryAsync**  
  
-   **GetObjectAsync**  
  
-   **PutInstanceAsync**  
  
 For more information on **IWbemProviderInit** and **IWbemServices**, see "COM API for WMI" in the MSDN Library at http://msdn.microsoft.com/library.  
  
 The WmiSna.mof and WmiSna_XP.mof files contain the WMISNA provider, and association and registration classes. You can access the WMISNA provider classes in the \root\MicrosoftHIS namespace.  
  
|Class|Description|  
|-----------|-----------------|  
|[MsSna_Domain](../core/mssna-domain-class.md)|Global properties that affect all servers in the group. Sometimes called a subdomain or OU.|  
|[MsSna_ServiceSNA](../core/mssna-servicesna-class.md)|SNA service implements the SNA protocol. Contains the connections and LU resources.|  
|[MsSna_ServiceTN3270](../core/mssna-servicetn3270-class.md)|TN3270 service enables clients to connect to a host via the TN3270 protocol.|  
|[MsSna_ServiceTN5250](../core/mssna-servicetn5250-class.md)|TN5250 service enables clients to connect via the TN5250 protocol to a host.|  
|[MsSna_ServicePrint](../core/mssna-serviceprint-class.md)|Host Print service contains print sessions.|  
|[MsSna_UserInfo](../core/mssna-userinfo-class.md)|Base class for a User or Group account configured in SNA.|  
|[MsSna_ConfiguredUser](../core/mssna-configureduser-class.md)|A User or Group account configured in SNA. Can determine access to LUs and pools.|  
|[MsSna_LogInUserAndGroups](../core/mssna-loginuserandgroups-class.md)|For the logged-on user, an enumeration returns the configured user and groups.|  
|[MsSna_Workstation](../core/mssna-workstation-class.md)|A workstation configured in SNA, specified by name or IP address. Can determine access to LUs and pools.|  
|[MsSna_Lu3270](../core/mssna-lu3270-class.md)|Base class for 3270 LU resource. Each 3270 LU must belong to a connection.|  
|[MsSna_LuDisplay](../core/mssna-ludisplay-class.md)|A 3270 LU display resource. Often used for terminal emulator access.|  
|[MsSna_LuLua](../core/mssna-lulua-class.md)|A 3270 LU LUA resource. Often used for programmatic access.|  
|[MsSna_TN3270Session](../core/mssna-tn3270session-class.md)|The part of the TN3270 session that specifies client configuration. References a SNA_LU_LUA class.|  
|[MsSna_TN3270Port](../core/mssna-tn3270port-class.md)|Describes a port with security properties.|  
|[MsSna_TN3270SessionIPFilter](../core/mssna-tn3270sessionipfilter-class.md)|An IP address/name assigned to a TN3270 session. Multiple IP address/name pairs of these can be assigned to one session.|  
|[MsSna_TN5250SessionIPFilter](../core/mssna-tn5250sessionipfilter-class.md)|An IP address/name assigned to a TN5250 session. Multiple IP address/name pairs of these can be assigned to one session.|  
|[MsSna_LuPassThrough](../core/mssna-lupassthrough-class.md)|One half of the dowstream LU/pool pairs. Represents a downstream LU/pool that is associated with a downstream connection.|  
|[MsSna_LuDown](../core/mssna-ludown-class.md)|A 3270 LU downstream resource. Reserved for use with downstream connections.|  
|[MsSna_LuPrint](../core/mssna-luprint-class.md)|A 3270 LU printer resource. Used by Print Session or by printer emulator.|  
|[MsSna_Pool](../core/mssna-pool-class.md)|Base class for 3270 LU pools. A pool is associated with one or more 3270 LUs.|  
|[MsSna_PoolDisplay](../core/mssna-pooldisplay-class.md)|The 3270 LU display pool.|  
|[MsSna_PoolLua](../core/mssna-poollua-class.md)|The 3270 LU LUA pool.|  
|[MsSna_PoolDown](../core/mssna-pooldown-class.md)|The 3270 LU downstream pool.|  
|[MsSna_LuAppcLocal](../core/mssna-luappclocal-class.md)|An APPC Local LU resource. Used for LU 6.2 protocol.|  
|[MsSna_LuAppcRemote](../core/mssna-luappcremote-class.md)|An APPC remote LU resource. Used for LU 6.2 protocol. References a connection.|  
|[MsSna_AppcMode](../core/mssna-appcmode-class.md)|An APPC Mode definition. Defines properties of an LU 6.2 session.|  
|[MsSna_Connection](../core/mssna-connection-class.md)|Base class for SNA connection. Belongs to an SNA service. May own 3270 LUs.|  
|[MsSna_Connection8022Dlc](../core/mssna-connection8022dlc-class.md)|A type of SNA connection that uses DLC 802.2 protocol over Token Ring or Ethernet.|  
|[MsSna_ConnectionSdlc](../core/mssna-connectionsdlc-class.md)|A type of SNA connection that uses SDLC protocol over dial-up or leased lines.|  
|[MsSna_ConnectionX25](../core/mssna-connectionx25-class.md)|A type of SNA connection that uses X.25 protocol over dial-up or leased lines.|  
|[MsSna_ConnectionChannel](../core/mssna-connectionchannel-class.md)|A type of SNA connection that uses Channel links.|  
|[MsSna_Cpic](../core/mssna-cpic-class.md)|A global CPI-C definition for APPC.|  
|[MsSna_TN5250Definition](../core/mssna-tn5250definition-class.md)|The definition of a TN5250 session.|  
|[MsSna_PrintSession](../core/mssna-printsession-class.md)|Base class for a print session on a Host Print service.|  
|[MsSna_PrintSession3270](../core/mssna-printsession3270-class.md)|Extends a Print session. Uses 3270 protocols to communicate with the host.|  
|[MsSna_PrintSessionAppc](../core/mssna-printsessionappc-class.md)|Extends a Print session. Uses APPC LU 6.2 protocols to communicate with the host.|  
|[MsSna_AppcPartner](../core/mssna-appcpartner-class.md)|A preconfigured combination of APPC Local LU, Remote LU, and Mode.|  
|[MsSna_AccountAssigned3270](../core/mssna-accountassigned3270-class.md)|Used to query for 3270 LUs assigned to a specific workstation or user.|  
|[MsSna_AccountAssignedLua](../core/mssna-accountassignedlua-class.md)|Used to query for LUA LUs assigned to a specific workstation or user.|  
|[MsSna_AccountAssigned3270Services](../core/mssna-accountassigned3270services-class.md)|Used to query for services on which a specific workstation or user has 3270 LUs/pools.|  
|[MsSna_AccountAssignedLuaServices](../core/mssna-accountassignedluaservices-class.md)|Used to query for services on which a specific workstation or user has LUA LUs/pools.|  
|[MsSna_AccountAvailableAppcLu](../core/mssna-accountavailableappclu-class.md)|For the logged-on user account and workstation, the assigned APPC LU resources.|  
|[MsSna_AdapterOnMachine](../core/mssna-adapteronmachine-class.md)|Associates an adapter with a computer.|  
|[MsSna_ConnectionOnServer](../core/mssna-connectiononserver-class.md)|Associates a connection with a server.|  
|[MsSna_Lu3270OnConnection](../core/mssna-lu3270onconnection-class.md)|Associates a 3270 LU with a connection.|  
|[MsSna_LuDisplayAssignedToUser](../core/mssna-ludisplayassignedtouser-class.md)|Associates a display LU with a user.|  
|[MsSna_LuPrintAssignedToUser](../core/mssna-luprintassignedtouser-class.md)|Associates a print LU with a user.|  
|[MsSna_LuLuaAssignedToUser](../core/mssna-luluaassignedtouser-class.md)|Associates an LUA LU with a user.|  
|[MsSna_PoolDisplayAssignedToUser](../core/mssna-pooldisplayassignedtouser-class.md)|Associates a display pool with a user.|  
|[MsSna_PoolLuaAssignedToUser](../core/mssna-poolluaassignedtouser-class.md)|Associates the pool LUA with a user.|  
|[MsSna_LuDisplayAssignedToWorkstation](../core/mssna-ludisplayassignedtoworkstation-class.md)|Associates a display LU with a workstation.|  
|[MsSna_LuPrintAssignedToWorkstation](../core/mssna-luprintassignedtoworkstation-class.md)|Associates a print LU with a workstation.|  
|[MsSna_LuLuaAssignedToWorkstation](../core/mssna-luluaassignedtoworkstation-class.md)|Associates an LUA LU with a workstation.|  
|[MsSna_PoolDisplayAssignedToWorkstation](../core/mssna-pooldisplayassignedtoworkstation-class.md)|Associates a display pool with a workstation.|  
|[MsSna_PoolLuaAssignedToWorkstation](../core/mssna-poolluaassignedtoworkstation-class.md)|Associates an LUA pool with a workstation.|  
|[MsSna_ConnectionUsingAdapter](../core/mssna-connectionusingadapter-class.md)|Associates a connection with an adapter.|  
|[MsSna_Lu3270AssignedToPool](../core/mssna-lu3270assignedtopool-class.md)|Associates a 3270 LU with a pool.|  
|[MsSna_PoolOnServer](../core/mssna-poolonserver-class.md)|Associates a pool with a server.|  
|[MsSna_ExtendedStatus](../core/mssna-extendedstatus-class.md)|Describes the extended status of a specified message.|