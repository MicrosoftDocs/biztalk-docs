---
title: "Command-Line Interface1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f27df562-c93a-4af0-91b8-6efb59b64236
caps.latest.revision: 4
---
# Command-Line Interface
In addition to the graphical user interfaces provided by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Setup and the SNA Manager, Host Integration Server offers a command-line interface. The command-line interface can be useful in certain situations, such as when you want to view a configuration setting quickly without starting the graphical interface, or when you want to store configuration commands in a command file so that they can be carried out easily in the future.  
  
 Before using the command-line interface, you must install Host Integration Server and run the SNA Manager at least once. This initializes important elements of the Host Integration Server configuration that cannot be controlled with the command-line interface.  
  
 You can use the command-line interface to modify an offline configuration file (as well as a regular on-site configuration file). However, when you work with an offline configuration file, validation of server names, link names, and user names cannot take place, and errors may result. For information about specifying the name of the configuration file to modify with the command-line interface, see [Specify the Subdomain Configuration File](../core/specify-the-subdomain-configuration-file1.md).  
  
 Other actions are also not available from the command-line. For example, you cannot use the command-line interface to configure ranges of LUs.  
  
 Certain Host Integration Server commands must be used with great care if the **/add** option is used with them. With these commands  **snacfg server**, **snacfg link**, and **snacfg user** the information you type must match existing information in your system or on the Windows domain.  
  
> [!IMPORTANT]
>  If you specify server names, link service names, adapter properties, or user names by using the /add option with snacfg server, snacfg link, or snacfg user, these names or properties must match existing names and properties in your installation, or a nonfunctioning configuration may result. To protect against errors with these commands, use the SNA Manager instead.  
  
## In This Section  
 [Snacfg Reference](../core/snacfg-reference1.md)  
  
 [Linkcfg Reference](../core/linkcfg-reference1.md)  
  
 [Kerberos Support](../core/kerberos-support2.md)