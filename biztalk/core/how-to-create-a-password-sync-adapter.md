---
title: "How to Create a Password Sync Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: caa5bd13-efd9-4544-b5df-17d01c6ac5d8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Password Sync Adapter
A password sync (PS) adapter is an application that uses the Password Sync Helper component to pass notifications to and from Enterprise Single Sign-On (SSO). Note that although the PS Helper component exposes a COM and a .NET Framework interface, your adapter does not necessarily have to be a COM component. You can design your adapter as a stand-alone process, a COM+ application, or a Windows service.  
  
### To create a password sync adapter  
  
1.  Inform Enterprise Single Sign-On service (ENTSSO) that your provider is active using `ISSOPSWrapper.InitializeAdapter`.  
  
     `InitializeAdapter` informs ENTSSO that a provider, usually the same provider that is making the call, is currently turned on, and therefore will be communicating password updates to and from the system. You can also use `InitializeAdapter` to activate other resources such as group adapters.  
  
2.  Send password updates to ENTSSO by using `ISSOPSWrapper.SendNotification`.  
  
     You must determine how you receive password updates from your non-Windows system. After you receive the update, you can pass the information on to ENTSSO using `SendNotification`. Note that `SendNotification` is not limited to sending password updates: the architecture of `SendNotification` also enables you to send other types of notifications.  
  
3.  Request password updates from ENTSSO by using `ISSOPSWrapper.ReceiveNotification`.  
  
     Because the password sync adapter is a pull technology, ENTSSO never calls your adapter. Instead, your adapter periodically calls `ReceiveNotification` to see whether any password updates are available. You can choose to set the WAIT flag on `ReceiveNotification`. Setting WAIT blocks the thread until a notification is available.  
  
     Note that ENTSSO delivers a password change to your adapter in plain text. It is the responsibility of the adapter to protect that password information against incorrect disclosure. It is also the responsibility of the adapter to protect itself against spoofing or attacks from other invalid sources, including spoofing of the Password Sync Helper component.  
  
     After you receive a password update from ENTSSO through the `pReceiveNotification` parameter, you must pass this information on to your non-Windows system. As with `SendNotification`, you must determine the best way to communicate with the remote server.  
  
4.  Turn off your adapter using `ISSOPSWrapper.ShutdownAdapter`.  
  
     `ShutdownApplication` should be the last method called by an adapter, and indicates that the adapter will no longer send or receive password updates to ENTSSO.  
  
     Note that ENTSSO buffers any password changes a user makes while the adapter is shut down, up to a buffer size limit.  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)   
 [Synchronizing Passwords](../core/synchronizing-passwords.md)