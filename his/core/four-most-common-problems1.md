---
title: "Four Most Common Problems1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee76392d-8ea0-4c5f-ac61-d0b6131ca0c0
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Four Most Common Problems
The four most common problems reported are as follows:  

1. **Setup or Upgrades**: The most frequently asked [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] questions are related to setup or upgrade issues. If you are connecting to an AS/400 via Token-Ring or Ethernet, make sure you read KB article Q112158 found at [http://go.microsoft.com/fwlink/?LinkId=14394](http://go.microsoft.com/fwlink/?LinkId=14394). If you are connecting to an AS/400 via an SDLC card, KB Article Q112159 found at [http://go.microsoft.com/fwlink/?LinkId=14395](http://go.microsoft.com/fwlink/?LinkId=14395) can be helpful. Examples of VTAM configurations for connecting to a mainframe can be found in the [Host Configuration](../core/host-configuration1.md) section. The configuration file (COM.CFG) contains almost all of the configuration information for the Host Integration Server environment. It is extremely important to back up this file before making changes.  

2. **Connectivity Issues**: If you are having a problem connecting to the host, determine where the problem originates. Because [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is the middle piece of a three-part connection, it helps to narrow the problem down to a Host Integration client, Host Integration Server issue, or a Host Integration Server host issue.  

3. **Host Printing**: For more information, see [Host Print Service Problems](../core/host-print-service-problems1.md).  

4. **APPC or LUA Application Failures**: See [APPC or LUA Application Failures](../core/appc-or-lua-application-failures2.md).
