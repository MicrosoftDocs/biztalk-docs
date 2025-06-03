---
description: "Learn more about: How to Log a Local User on to a Non-Windows Application"
title: "How to Log a Local User on to a Non-Windows Application"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Log a Local User on to a Non-Windows Application
After you set up your user with an affiliate application, you can use Single Sign-On (SSO) to access the external user name and credentials of the current user. Using these credentials, you can then log your user on to the affiliate application that is running on a host server.

> [!NOTE]
>  In addition to setting the appropriate security protocols for SSO, you might also need to set additional security to allow your application to call SSO in the correct security context. If your application cannot call SSO in the correct security context, SSO will deny access to your application.

### To set the security context for an SSO application

1.  Identify what credentials your application needs to run successfully.

     For example, an application that uses Web services or.NET Framework remoting hosted in IIS needs to impersonate the client in order to pass the appropriate credentials on to SSO.

2.  Confirm that the relevant security settings, such as those on virtual directories, application pools, and web.config files, are set to provide your application with those credentials.

     For more information about how to set security credentials, see [Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](/previous-versions/msp-n-p/ff649266(v=pandp.10)).

     For more information about passing credentials for an ASP.NET Web service, see [HOW TO: Pass Current Credentials to an ASP.NET Web Service](https://support.microsoft.com/default.aspx?scid=kb;en-us;813834).

### To log a local user on to a host application

1.  Receive the request to log the current user on to an application running on the host server.

     It is your responsibility to determine how the current user requests to be logged on to a host application.

2.  Retrieve the credentials for the current user who is using `ISSOLookup1.GetCredentials` or `ISSOLookup2.GetCredentials`.

     You must supply the name of the host application together with any relevant flags. `GetCredentials` returns the associated user name and credentials for the host application.

     Note that you can use either `ISSOLookup1` or `ISSOLookup2`. The only difference is that `ISSOLookup2` also has a method for logging a remote user on to a local windows application.

3.  Use the external user name and credentials to log on to the host application.

     It is your responsibility to determine how to use the credentials to log on to the host application.

## See Also
 [How to Log a Remote User on to a Local Application](../esso/how-to-log-a-remote-user-on-to-a-local-application.md)
