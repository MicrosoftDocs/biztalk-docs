---
description: "Learn more about: How to Log a Remote User on to a Local Application"
title: "Log a Remote User on to a Local Application"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Log a Remote User on to a Local Application
The other main feature of Enterprise Single Sign-On service (ENTSSO) is supporting a host-initiated process (HIP). ENTSSO interacts with HIP when a remote user tries to access a local Windows resource. Using ENTSSO, you can receive the request from the host user and request access to the local Windows application.  
  
## Log a remote user on to a local Windows application  
  
1.  Receive the request from the remote user.  
  
     It is your responsibility to determine how to retrieve a request from the remote user.  
  
2.  Request that the remote user be given access to the specified affiliate application, using `ISSOLookup2.LogonExternalUser`.  
  
     `LogonExternalUser` passes in the name of the application the external user wishes to access, the name of the external user, the associated credentials for the external user, and any relevant flags. If successful, `LogonExternalUser` returns a handle to a Windows access token.  
  
     The remote user must already be identified in the Single Sign-On database, have their credentials in the database, and be associated with an affiliate application. Otherwise, `LogonExternalUser` returns an error. You can keep the user names and credentials up to date using Password Sync.  
  
     In addition, you must have protocol transition enabled.  
  
3.  Use the Windows handle returned from `LogonExternalUser` to impersonate the user that the token represents.  
  
## See Also  
 [How to Log a Local User on to a Non-Windows Application](../esso/how-to-log-a-local-user-on-to-a-non-windows-application.md)   
 [ISSOLookup2.LogonExternalUser Method](../esso/issolookup2-logonexternaluser-method.md)
