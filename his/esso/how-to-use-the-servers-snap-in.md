---
description: "Learn more about: How to Use the Servers Snap-In"
title: "How to Use the Servers Snap-In"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Use the Servers Snap-In
This version of Enterprise Single Sign-On (SSO) includes the ENTSSO Servers Snap-In, which allows you to view, monitor, and perform certain actions on your ENTSSO Server through the Windows interface.  
  
> [!NOTE]
>  If your system has a firewall and your server name uses the FQDN format, you may not be able to contact the server. Instead, you must specify the NetBIOS name or the associated IP address.  
  
### To use the ENTSSO Servers Snap-In  
  
1.  Open Enterprise Single Sign-On.  
  
2.  In the Scope pane, click the **Servers** node.  
  
     The following information is displayed in the Results pane.  
  
    -   **Name**: Name specified.  
  
    -   **Status**: Status of the ENTSSO service (Online, Offline, Pending, Started, Stopped, Start Pending, Stop Pending).  
  
    -   **Date**: Date when information was obtained.  
  
    -   **Time**: Time when information was obtained.  
  
    -   **SSO Server**: Fully qualified name of server.  
  
    -   **Service Account**: ENTSSO service account.  
  
    -   **SSO Database**: ENTSSO Credential Database with which this server is communicating.  
  
    -   **Secret Server**: Indicates whether the Secret Server module is running.  
  
    -   **Password Sync**: Indicates whether Password Sync is installed.  
  
    -   **Computer**: NETBIOS name of computer.  
  
    -   **Event counts**: Info/Warning/Errors event count. Resetting this will start the counter from 0.  
  
    -   **Version of SSO installed**: Version number of ENTSSO.exe. Also indicates whether this is 32-bit (x86) or 64-bit (x64).  
  
### To start or stop the server service  
  
-   In the ENTSSO Servers Snap-In, right-click the server and click **Start** or **Stop**.  
  
### To display information for one server  
  
-   In the Server tree, click the server.  
  
     The information is displayed in the results pane.  
  
### To add a server  
  
-   Right-click in the Scope pane, and then click **Add Server**.  
  
     The **Add Server** dialog box appears. Type or browse to the server you want to add.  
  
     In certain Workgroup environments, clicking the **Browse** button will cause this dialog box to close. Instead of using the **Browse** button, simply type the server name in the box.  
  
### To view or change server properties  
  
-   In the Server tree, right-click the server, and click **Properties**.  
  
     The **Server Properties** dialog box appears. You can view or change information in the following tabs:  
  
    -   **Audit Levels**  
  
    -   **SSO Database**  
  
    -   **SSO Service**  
  
    -   **Password Sync**  
  
    -   **Advanced**  
  
## See Also  
 [Enterprise Single Sign-On](../esso/enterprise-single-sign-on1.md)
