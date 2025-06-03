---
description: "Learn more about: How to Configure Active Directory During Host Integration Server Installation"
title: "How to Configure Active Directory During Host Integration Server Installation1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Configure Active Directory During Host Integration Server Installation
[!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] participation in Active Directory is accomplished by the SNA Gateway service and the Host Integration Server WMI (Windows Management Instrumentation) provider.  
  
 With [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], there are two mechanisms that will deliver SNA client resource location. One is sponsor connections, which are based on direct communication with a Host Integration Server. The second uses Windows Active Directory.  
  
 If you want to use Active Directory instead of SNA subdomains, you must add the Host Integration Server schema to the Windows domain schema before installing Host Integration Server.  
  
 The Windows schema is extended by running a command-line utility. The following procedure adds the Host Integration Server schema to the Windows domain schema:  
  
### To extend the Active Directory schema  
  
1.  Make sure you are logged on as a user who is a member of the **Schema Admins**.  
  
2.  From **Support\ActiveDir** folder in the installation media, copy **Hiserver.schema** and the command-line tool **addschma.exe** for the appropriate processor type of your system.  
  
3.  From a command prompt launched with Administrator rights, run the following command:  
  
     `addschma hiserver.schema`  
  
> [!NOTE]
>  If you do not successfully add the Host Integration Server schema, you will not be able to use Active Directory, but you can still configure a Host Integration Server client to use SNA subdomains and sponsor connections. For more information, see [Host Integration Server Client and SNA Communications](../core/host-integration-server-client-and-sna-communications2.md).  
  
 Configuring Host Integration Server to use Active Directory is performed during installation. Selecting Support Active Directory Clients, and then entering an Organizational Unit (OU) adds the following services to the ServerResources container for that OU:  
  
-   SNAServer Service  
  
-   SNAWMI Provider Service  
  
-   SNABase Service  
  
-   MngAgent Service  
  
## See Also  
 [Active Directory Services](../core/active-directory-services2.md)
