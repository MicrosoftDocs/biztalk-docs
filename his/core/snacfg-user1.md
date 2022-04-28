---
description: "Learn more about: Snacfg User"
title: "Snacfg User1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e53fb049-0f84-4a46-96cb-9e3a504ef291
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Snacfg User
## Purpose  
 Enables you to view, modify settings for, or delete users recognized by [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. Also lets you assign LUs or LU pools to 3270 users, or assign default LUs to 5250 users.  
  
 In addition, **snacfg user** enables you to add users to the list recognized by Host Integration Server. However, it is recommended that you use the SNA Manager, not **snacfg user**, when adding users.  
  
> [!IMPORTANT]
>  If you add user names by using the **/add** option with **snacfg user**, these names must match existing user account names in the Windows domain, or a nonfunctioning configuration may result. To protect against errors with **snacfg user**, use the SNA Manager, instead.  
  
 Before assigning LUs or LU pools to users, you must first configure the LUs or LU pools.  
  
> [!NOTE]
>  Configuration settings specified with snacfg user correspond to user or group settings configured with the SNA Manager.  
  
## Syntax  
  
```  
  
        [configpath]  [configpath] username [configpath] username [options]  
[configpath]  [configpath] username [options]  
[configpath] username  
```  
  
 where  
  
 **#** *configpath*  
 Specifies the path of the configuration file to view or change. If the configuration path is omitted, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will attempt to access the configuration file on the local system, using the path \Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG.  
  
 **/list**  
 Generates a list of the 3270 users recognized by Host Integration Server.  
  
 *domain/username*  
 Specifies the domain and name of the user to add, view, change settings for, or delete.  
  
 For adding 3270 users, the recommended method is to use the SNA Manager, not **snacfg user**. If you are adding or removing a user, *username* must match the name in the user's account on the Windows domain specified by *domain*.  
  
 **/add**  
 Adds a user called *username* to the list of 3270 users recognized by Host Integration Server. The user must already have an account on the Windows domain or on the local system.  
  
 For adding 3270 users, the recommended method is to use the SNA Manager, not **snacfg user**.  
  
 **/validate**  
 Attempts to fill in any SIDs that are missing from user or group listings in the Host Integration Server configuration file. If the SIDs can be obtained from user accounts in the Windows domain for each user, the SIDs will be added to the listings in the Host Integration Server configuration.  
  
 Run **snacfg user /validate** after working offline and adding users to the configuration, so that the user listings in Host Integration Server will be functional.  
  
 **/delete**  
 Deletes *username*.  
  
## Options for Users of 3270 Emulators  
 **/insert:** *luname*[, *luname*,...]  
 Assigns the specified 3270 or LUA LUs or pools to the user. Separate multiple names with commas.  
  
 **/remove:** *luname*[, *luname*,...]  
 Deletes the assignment of 3270 or LUA LUs or pools to the user. Separate multiple names with commas.  
  
 **/insertrlu:** *luname*[, *luname*,...]  
 Assigns APPC Remote LUs to the user. Separate multiple names with commas. The name *rluname* can be either the RLU alias or its fully-qualified name of the form "*netname.luname*".  
  
 **/removerlu:** *luname*[, *luname*,...]  
 Deletes the assignment of APPC Remote LUs to the user. Separate multiple names with commas. The name *rluname* can be either the RLU alias or its fully-qualified name of the form "*netname.luname*".  
  
 **/domain:** *domainname*  
 Specifies the Windows domain in which the user account is found. For all actions involving the domain name associated with a user account, the recommended method is to use the SNA Manager, not **snacfg user**. If an incorrect domain name is specified with **snacfg user**, a nonfunctioning configuration may result.  
  
 **/comment:**" *text*"  
 Adds an optional comment for the specified user. The comment can contain as many as 25 characters. The quotes must be included.  
  
 **/encrypt:{ yes &#124; no }**  
 Specify YES to enable data encryption between the server and client.  
  
## Options for Users of TPs or 5250 Emulators  
 **/defloclu:** *LUalias*  
 Specifies the default local APPC LU for this user or group. Both the user (or group) name and the LU alias must already be configured in Host Integration Server. If **/defloclu:** is typed without *LUalias*, the user or group record is cleared of any default local LU.  
  
 **/defremlu:** *LUalias*  
 Specifies the default remote APPC LU for this user or group. Both the user (or group) name and the LU alias must already be configured in Host Integration Server. If **/defremlu:** is typed without *LUalias*, the user or group record is cleared of any default remote LU.  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)
