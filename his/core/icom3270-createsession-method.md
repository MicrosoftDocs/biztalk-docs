---
title: "Icom3270.createSession Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a70c8f2-1770-433b-849e-34bc5ef856e6
caps.latest.revision: 4
---
# Icom3270.createSession Method
The creaetSession method creates a new 3270 session.  
  
## Syntax  
  
```  
  
void CreateSession(  
   string connectionStr,   
   out object sessionHandle  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`connectionStr`|NULL-terminated string containing the connection properties of the new session. The string is presented in a space-delineated "PROPERTY=VALUE" format. Property names and values are case-insensitive. For more information, see Icom3270 Session Properties.|  
|`sessionHandle`|When this method returns, contains a pointer to the IUnknown interface for the comSNA3270 session. This session represents the underlying SNA session.<br /><br /> You will use `sessionHandle` in Icom3270.Connect to connect the com3270 object with the session.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|C3270_S_LINKINAC|The SNA session was successfully created, but the underlying SNA connection is not yet active.<br /><br /> You should use Icom3270.wait to wait for the session to become active.|  
|C3270_S_PUINAC|The SNA session was successfully created, but the SNA PU is not yet active.<br /><br /> You should use Icom3270.wait to wait for the session to become active.|  
|C3270_S_LUINAC|The SNA session was successfully created, but he LU is not yet active.<br /><br /> You should use Icom3270.wait to wait for the session to become active.|  
|C3270_S_TN3270E|The TN3270 session was successfully created in TN3270E, or RFC 1647, mode.|  
|C3270_S_TN3270|The TN3270 session was successfully created in TN3270, or RFC 1576, mode.|  
|S_OK|The SNA or local session was successfully created and the LU_SSCP session is active and ready to receive input.|  
|C3280_E_BADPARAM|`connectionStr` contained an invalid property setting.|  
|C3270_E_NOFREELU|`luname` specified an SNA Server LU pool. However, there are no LUs free in that pool.|  
|C3270_E_LUINUSE|`luname` specified an SNA server LU pool. However, the LU is currently in use by another application.|  
|C3270_E_LUNOTFOUND|The LU or pool name does not exist.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
|C3270_E_ACCESSDENIED|The user account for the client does not have permission to use the requested LU or pool.|  
|C3270_E_NOTFOUND|The remote system specified by the IP property in `connectionStr` could not be located.|  
|C3270_E_REFUSED|The remote system specified by the IP and PORT properties in `connectionSTR` refused the connection string.|  
  
## Exceptions  
  
## Remarks  
 The following list describes the location of the session, as determined by to the session type. A session type is also known as the MODE property.  
  
-   Local session - created on the client.  
  
-   SNA session - created on the SNA server machine that is configured with the requested LU or pool.  
  
-   TN3270 session - created on the COM server specified by the SERVER property.