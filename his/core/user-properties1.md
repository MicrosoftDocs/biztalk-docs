---
description: "Learn more about: User Properties"
title: "User Properties1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_User"
---
# User Properties
**User Name**  
 Provided for information only. This field cannot be changed here.  
  
 **Domain**  
 Provided for information only. This field cannot be changed here.  
  
 **Comment**  
 Optionally, type a comment of up to 25 characters.  
  
 **Use Client/Server Encryption**  
 Check this box to enable encryption between the client system and [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
 **Allow Access To Dynamically Created Remote APPC LUs**  
 Check this box to let this user or group use dynamically created APPC LUs.  
  
## APPC Defaults  
 **Local APPC LU**  
 If this user will be using APPC programs (TPs, 5250 emulators, or APPC applications), you can choose a default local APPC LU to be used when the user starts such programs.  
  
 Avoid assigning a default local APPC LU to the group "Everyone". Instead, to make a local APPC LU available to any user, when configuring the local LU, select the check box labeled **Member of Default Outgoing Local APPC LU Pool** on the **Advanced** tab of **Local LU Properties**.  
  
 **Remote APPC LU**  
 If this user will be using APPC programs (TPs, 5250 emulators, or APPC applications), you can choose a default remote APPC LU to be used when the user starts such programs.  
  
 To accept the settings, click **OK**; to exit the dialog box without accepting the settings, click **Cancel**.  
  
 When you assign default APPC LUs to user and group accounts with overlapping memberships, some of these assignments override others.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)
