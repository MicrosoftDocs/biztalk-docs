---
title: "Use the -print Option1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2ed5bd9-e68a-4fc0-a82b-d0ada122e57c
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Use the /print Option
The **/print** option can make it easier to carry out repetitive configuration actions, if you have a detailed understanding of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] configurations and of the **snacfg** command. Here are some ways of using the **/print** option:  
  
 **Creating a new configuration**  
 You can generate a **snacfg** command file corresponding to an entire configuration file, modify the command file, and use it to create a new configuration file for another subdomain or site. To generate the commands for an entire configuration file, use the syntax shown in the first example in the previous section; that is, omit all **snacfg** modifiers (such as **connection** or **lu**).  
  
 **Creating a template to use for expanding one or more configurations**  
 You can generate a **snacfg** command file that corresponds to a useful element of an existing configuration (for example, a 3270 LU in a configuration). Then you can modify the file and use it to add one or many similar elements to an existing configuration. Such a command file acts as a template for the element that it contains.  
  
 **Modifying a configuration**  
 You can generate a **snacfg** command file that corresponds to some part of an existing configuration (for example, an 802.2 connection in a configuration), modify the command file, and use it to modify the configuration file from which it came. This involves removing the **/add** option from lines in the command file, and making other changes that require a detailed understanding of the commands in the file.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)