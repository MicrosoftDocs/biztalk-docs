---
description: "Learn more about: Password Sync Programming Architecture"
title: "Password Sync Programming Architecture"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Password Sync Programming Architecture
A password sync adapter uses a pull model for interacting with the rest of the Enterprise Single Sign-On system: that is, the adapter actively receives password changes from the Enterprise Single Sign-On (ENTSSO) service and also from the non-Windows system. Similarly, the adapter pushes password changes received from one system to the other. With this model, your adapter interacts with three architectural components: the ENTSSO architecture, the Password Sync (PS) Helper component, and a specified non-Windows system.  
  
## Enterprise Single Sign-On Architecture  
 ENTSSO is the service that implements the Enterprise Single Sign-On technology, and runs as a local service on the same system as your adapter. Therefore, communication between the adapter and ENTSSO is always local. However, a password sync adapter runs in a separate process from the ENTSSO service.  
  
 ENTSSO uses the configuration store to store configuration information for an adapter. The Application Users account of a configuration store application corresponds to the access account. When an adapter calls into ENTSSO, ENTSSO checks that the adapter is within the configured access account for that adapter. The access account must be a (local or domain) group account.  
  
 Because ENTSSO stores information about an adapter, the adapter can identify itself to ENTSSO by its adapter name. The adapter name corresponds to the configuration store application name and the configuration store identifier used to store the adapter properties. Therefore, adapters must know only their adapter name to access configuration information and to correctly identify themselves to the ENTSSO system at run time.  
  
## Password Sync Helper  
 Password Sync (PS) Helper is a COM component provided by ENTSSO. PS Helper runs in-process with the password sync adapter, and exposes ISSOPSWrapper. Your adapter can call either interface to communicate with the ENTSSO service. The PS Helper passes communications to and from ENTSSO using encrypted (packet privacy) lightweight remote procedure call (LRPC). Although the communications are mainly for password updates, you can also use the interfaces to pass other types of notifications between the adapter and ENTSSO. Because PS Helper runs as a singleton value per process, it is possible for multiple adapters to call the same PS Helper object from within the same adapter process. For more information about using PS Helper programmatically, see [Synchronizing Passwords](../esso/synchronizing-passwords.md).  
  
## Non-Windows System  
 The non-Windows system is the remote computer your adapter interacts with. How you interact with the non-Windows system is up to you.  
  
## See Also  
 [Password Sync Adapters](../esso/password-sync-adapters.md)
