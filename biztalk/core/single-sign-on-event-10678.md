---
title: "Single Sign-On: Event 10678 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6af92ce1-fdac-432f-be6b-cf8958aee776
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Single Sign-On: Event 10678
## Details  
  
|||  
|-|-|  
|Product Name|Enterprise Single Sign-On|  
|Product Version|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|Event ID|10678|  
|Event Source|ENTSSO|  
|Component|N\A|  
|Symbolic Name|SSO_WARN_PASSWORD_MISMATCH|  
|Message Text|External password change. The old password supplied by the adapter does not match the existing password for the external account.%r<br /><br /> Tracking ID: %1%r<br /><br /> Adapter: %2%r<br /><br /> Application Name: %3%r<br /><br /> External Account: %4|  
  
## Explanation  
 This Warning event indicates that the old password supplied by the adapter does not match the existing password for the external account.  
  
## User Action  
 To resolve this warning do the following:  
  
-   Determine which Applications were assigned to this Adapter (name in event log message) and then use the SSO administration tools to set the external credentials for this external account. You must set the external password (for the given account) in all of those Applications.  
  
## More info
  
-   [Password Synchronization](../core/password-synchronization2.md)  
  
-   **Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]