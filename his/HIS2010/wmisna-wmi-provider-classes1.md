---
title: "WMISNA WMI Provider Classes1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dca06f9-bf0a-42ec-a55f-507de3736ccb
caps.latest.revision: 4
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
|[MsSna_Domain](../HIS2010/mssna-domain-class1.md)|Global properties that affect all servers in the group. Sometimes called a subdomain or OU.|  
|[MsSna_ServiceSNA](../HIS2010/mssna-servicesna-class2.md)|SNA service implements the SNA protocol. Contains the connections and LU resources.|  
|[MsSna_ServiceTN3270](../HIS2010/mssna-servicetn3270-class2.md)|TN3270 service enables clients to connect to a host via the TN3270 protocol.|  
|[MsSna_ServiceTN5250](../HIS2010/mssna-servicetn5250-class2.md)|TN5250 service enables clients to connect via the TN5250 protocol to a host.|  
|[MsSna_ServicePrint](../HIS2010/mssna-serviceprint-class2.md)|Host Print service contains print sessions.|  
|[MsSna_UserInfo](../HIS2010/mssna-userinfo-class1.md)|Base class for a User or Group account configured in SNA.|  
|[MsSna_ConfiguredUser](../HIS2010/mssna-configureduser-class1.md)|A User or Group account configured in SNA. Can determine access to LUs and pools.|  
|[MsSna_LogInUserAndGroups](../HIS2010/mssna-loginuserandgroups-class1.md)|For the logged-on user, an enumeration returns the configured user and groups.|  
|[MsSna_Workstation](../HIS2010/mssna-workstation-class2.md)|A workstation configured in SNA, specified by name or IP address. Can determine access to LUs and pools.|  
|[MsSna_Lu3270](../HIS2010/mssna-lu3270-class1.md)|Base class for 3270 LU resource. Each 3270 LU must belong to a connection.|  
|[MsSna_LuDisplay](../HIS2010/mssna-ludisplay-class1.md)|A 3270 LU display resource. Often used for terminal emulator access.|  
|[MsSna_LuLua](../HIS2010/mssna-lulua-class1.md)|A 3270 LU LUA resource. Often used for programmatic access.|  
|[MsSna_TN3270Session](../HIS2010/mssna-tn3270session-class2.md)|The part of the TN3270 session that specifies client configuration. References a SNA_LU_LUA class.|  
|[MsSna_TN3270Port](../HIS2010/mssna-tn3270port-class1.md)|Describes a port with security properties.|  
|[MsSna_TN3270SessionIPFilter](../HIS2010/mssna-tn3270sessionipfilter-class1.md)|An IP address/name assigned to a TN3270 session. Multiple IP address/name pairs of these can be assigned to one session.|  
|[MsSna_TN5250SessionIPFilter](../HIS2010/mssna-tn5250sessionipfilter-class2.md)|An IP address/name assigned to a TN5250 session. Multiple IP address/name pairs of these can be assigned to one session.|  
|[MsSna_LuPassThrough](../HIS2010/mssna-lupassthrough-class2.md)|One half of the dowstream LU/pool pairs. Represents a downstream LU/pool that is associated with a downstream connection.|  
|[MsSna_LuDown](../HIS2010/mssna-ludown-class1.md)|A 3270 LU downstream resource. Reserved for use with downstream connections.|  
|[MsSna_LuPrint](../HIS2010/mssna-luprint-class2.md)|A 3270 LU printer resource. Used by Print Session or by printer emulator.|  
|[MsSna_Pool](../HIS2010/mssna-pool-class2.md)|Base class for 3270 LU pools. A pool is associated with one or more 3270 LUs.|  
|[MsSna_PoolDisplay](../HIS2010/mssna-pooldisplay-class1.md)|The 3270 LU display pool.|  
|[MsSna_PoolLua](../HIS2010/mssna-poollua-class1.md)|The 3270 LU LUA pool.|  
|[MsSna_PoolDown](../HIS2010/mssna-pooldown-class1.md)|The 3270 LU downstream pool.|  
|[MsSna_LuAppcLocal](../HIS2010/mssna-luappclocal-class2.md)|An APPC Local LU resource. Used for LU 6.2 protocol.|  
|[MsSna_LuAppcRemote](../HIS2010/mssna-luappcremote-class2.md)|An APPC remote LU resource. Used for LU 6.2 protocol. References a connection.|  
|[MsSna_AppcMode](../HIS2010/mssna-appcmode-class1.md)|An APPC Mode definition. Defines properties of an LU 6.2 session.|  
|[MsSna_Connection](../HIS2010/mssna-connection-class1.md)|Base class for SNA connection. Belongs to an SNA service. May own 3270 LUs.|  
|[MsSna_Connection8022Dlc](../HIS2010/mssna-connection8022dlc-class1.md)|A type of SNA connection that uses DLC 802.2 protocol over Token Ring or Ethernet.|  
|[MsSna_ConnectionSdlc](../HIS2010/mssna-connectionsdlc-class2.md)|A type of SNA connection that uses SDLC protocol over dial-up or leased lines.|  
|[MsSna_ConnectionX25](../HIS2010/mssna-connectionx25-class2.md)|A type of SNA connection that uses X.25 protocol over dial-up or leased lines.|  
|[MsSna_ConnectionChannel](../HIS2010/mssna-connectionchannel-class2.md)|A type of SNA connection that uses Channel links.|  
|[MsSna_Cpic](../HIS2010/mssna-cpic-class2.md)|A global CPI-C definition for APPC.|  
|[MsSna_TN5250Definition](../HIS2010/mssna-tn5250definition-class1.md)|The definition of a TN5250 session.|  
|[MsSna_PrintSession](../HIS2010/mssna-printsession-class1.md)|Base class for a print session on a Host Print service.|  
|[MsSna_PrintSession3270](../HIS2010/mssna-printsession3270-class1.md)|Extends a Print session. Uses 3270 protocols to communicate with the host.|  
|[MsSna_PrintSessionAppc](../HIS2010/mssna-printsessionappc-class1.md)|Extends a Print session. Uses APPC LU 6.2 protocols to communicate with the host.|  
|[MsSna_AppcPartner](../HIS2010/mssna-appcpartner-class1.md)|A preconfigured combination of APPC Local LU, Remote LU, and Mode.|  
|[MsSna_AccountAssigned3270](../HIS2010/mssna-accountassigned3270-class1.md)|Used to query for 3270 LUs assigned to a specific workstation or user.|  
|[MsSna_AccountAssignedLua](../HIS2010/mssna-accountassignedlua-class2.md)|Used to query for LUA LUs assigned to a specific workstation or user.|  
|[MsSna_AccountAssigned3270Services](../HIS2010/mssna-accountassigned3270services-class2.md)|Used to query for services on which a specific workstation or user has 3270 LUs/pools.|  
|[MsSna_AccountAssignedLuaServices](../HIS2010/mssna-accountassignedluaservices-class2.md)|Used to query for services on which a specific workstation or user has LUA LUs/pools.|  
|[MsSna_AccountAvailableAppcLu](../HIS2010/mssna-accountavailableappclu-class2.md)|For the logged-on user account and workstation, the assigned APPC LU resources.|  
|[MsSna_AdapterOnMachine](../HIS2010/mssna-adapteronmachine-class1.md)|Associates an adapter with a computer.|  
|[MsSna_ConnectionOnServer](../HIS2010/mssna-connectiononserver-class1.md)|Associates a connection with a server.|  
|[MsSna_Lu3270OnConnection](../HIS2010/mssna-lu3270onconnection-class2.md)|Associates a 3270 LU with a connection.|  
|[MsSna_LuDisplayAssignedToUser](../HIS2010/mssna-ludisplayassignedtouser-class2.md)|Associates a display LU with a user.|  
|[MsSna_LuPrintAssignedToUser](../HIS2010/mssna-luprintassignedtouser-class1.md)|Associates a print LU with a user.|  
|[MsSna_LuLuaAssignedToUser](../HIS2010/mssna-luluaassignedtouser-class2.md)|Associates an LUA LU with a user.|  
|[MsSna_PoolDisplayAssignedToUser](../HIS2010/mssna-pooldisplayassignedtouser-class2.md)|Associates a display pool with a user.|  
|[MsSna_PoolLuaAssignedToUser](../HIS2010/mssna-poolluaassignedtouser-class1.md)|Associates the pool LUA with a user.|  
|[MsSna_LuDisplayAssignedToWorkstation](../HIS2010/mssna-ludisplayassignedtoworkstation-class1.md)|Associates a display LU with a workstation.|  
|[MsSna_LuPrintAssignedToWorkstation](../HIS2010/mssna-luprintassignedtoworkstation-class2.md)|Associates a print LU with a workstation.|  
|[MsSna_LuLuaAssignedToWorkstation](../HIS2010/mssna-luluaassignedtoworkstation-class1.md)|Associates an LUA LU with a workstation.|  
|[MsSna_PoolDisplayAssignedToWorkstation](../HIS2010/mssna-pooldisplayassignedtoworkstation-class2.md)|Associates a display pool with a workstation.|  
|[MsSna_PoolLuaAssignedToWorkstation](../HIS2010/mssna-poolluaassignedtoworkstation-class1.md)|Associates an LUA pool with a workstation.|  
|[MsSna_ConnectionUsingAdapter](../HIS2010/mssna-connectionusingadapter-class2.md)|Associates a connection with an adapter.|  
|[MsSna_Lu3270AssignedToPool](../HIS2010/mssna-lu3270assignedtopool-class1.md)|Associates a 3270 LU with a pool.|  
|[MsSna_PoolOnServer](../HIS2010/mssna-poolonserver-class1.md)|Associates a pool with a server.|  
|[MsSna_ExtendedStatus](../HIS2010/mssna-extendedstatus-class2.md)|Describes the extended status of a specified message.|