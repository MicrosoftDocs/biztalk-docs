---
title: "ISSOConfigOM.GetServerStatus | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9cbc817c-108c-4a5e-a3cf-c7f1354d80e6
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOConfigOM.GetServerStatus
The **GetServerStatus** method describes the status of the current server.  
  
## Syntax  
  
```vb  
  
GetServerStatus(  
flags As Integer,   
ssoServerName As String,   
sqlServer As String,   
sqlDatabase As String,   
serviceAccount As String,   
computerNameCluster As String,   
computerNameNode As String,   
eventCountInformational As Integer,   
eventCountWarning As Integer,   
eventCountError As Integer,   
versionInfoM As Integer,   
versionInfoL As Integer,   
auditLevelN As Integer,   
auditLevelP As Integer,   
passwordSyncAge As Integer,   
statusFlags As Integer  
);  
  
```  
  
```cpp#  
  
HRESULT GetServerStatus(  
int flags,   
BSTR ssoServerName,   
BSTR sqlServer,   
BSTR sqlDatabase,   
BSTR serviceAccount,   
BSTR computerNameCluster,   
BSTR computerNameNode,   
BSTR eventCountInformational,   
int eventCountWarning,   
int eventCountError,   
int versionInfoM,   
int versionInfoL,   
int auditLevelN,   
int auditLevelP,   
int passwordSyncAge,   
int statusFlags  
);  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`flags`|Not used in this version. Should be set to zero.|  
|`ssoServerName`|Returns a string containing the current SSO server name.|  
|`sqlServer`|Returns a string containing the name of the SQL server of the current server.|  
|`sqlDatabase`|Returns a string containing the name of the SQL database of the current server.|  
|`serviceAccount`|Returns a string containing the current service account.|  
|`computerNameCluster`|Returns a string containing the name of the current computer cluster.|  
|`computerNameNode`|Returns the name of the current computer.|  
|`eventCountInformational`|Returns an integer containing information regarding the event count.|  
|`eventCountWarning`|Returns an integer containing the event count warning.|  
|`eventCountError`|Returns an integer containing the event count error.|  
|`versionInfoM`|Returns an integer containing the MSB version info.|  
|`versionInfoL`|Returns an integer containing the LSB version info.|  
|`auditLevelN`|Returns an integer containing the negative audit level.|  
|`auditLevelP`|Returns an integer containing the positive audit level.|  
|`passwordSyncAge`|Returns an integer containing the password sync age.|  
|`statusFlags`|Returns an integer containing the status flags. For more information, see SSOStatusFlags.|  
  
## Property Value/Return Value  
 [C++] This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 [Visual Basic] Not Applicable.  
  
## Exceptions  
 [C++] This method returns an HRESULT containing one of the values in the following table.  
  
 [Visual Basic] This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDREG|An invalid parameter was detected.|