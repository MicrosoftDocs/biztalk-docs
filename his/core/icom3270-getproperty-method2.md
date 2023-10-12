---
description: "Learn more about: Icom3270.getProperty Method"
title: "Icom3270.getProperty Method2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Icom3270.getProperty Method
The getProperty method describes the properties of a session.  
  
## Syntax  
  
```  
  
void GetProperty(  
   string PropertyName,  
   out object value  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`propertyName`|The name of the property to be returned.|  
|`propertyValue`|When this method returns, contains the value of the specified property.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|C3270_E_NOT_CONNECTED|The com3270 client is not connected to a session object through Icom3270.Connect.|  
|C3270_E_INVALIDMODE|The property described in `propertyName` is not valid for the session MODE setting.|  
  
## Exceptions  
  
## Remarks  
 You can use getProperty to determine the name of the pooled LU selected for the session when an SNA session was originally created using an SNA server pool name. For more information, see Supported com3270 Session Properties.
