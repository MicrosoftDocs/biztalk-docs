---
title: "IP Settings2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54a1c7f7-7bc0-4f5d-820d-d5a91da755eb
caps.latest.revision: 4
---
# IP Settings
The IP settings assigned to an LUA LU or pool will allow TN3270 clients to connect to that LUA LU or pool. By default, the LUA LU or pool is not assigned an IP address or a subnet mask. This will allow any TN3270 client to use the LUA LUs or pools.  
  
 If you want to restrict an LUA LU or pool to one or more specific TN3270 clients, you should determine the IP address or host name of the client computers that will use these LUA LUs or pools. For client computers using Windows, you can determine the IP address, subnet mask, and host name by typing **ipconfig/all** from the command prompt on the client computer.  
  
 If a workstation has a name that can be resolved using name resolution, it can be used in place of IP addresses. For example, if a workstation name is Giraffe and if the IP name list contains that name, it will map to the correct IP address. Name resolution works with WINS, DHCP, or similar name resolution services. For more information regarding WINS and DHCP, see your Windows documentation.  
  
 You can modify, delete, or add IP addresses and subnet masks within LUA LUs or pools. If you want to change the configuration of multiple LUA LUs, you can only change properties such as display types, the IP address, and subnet mask that the LUA LUs have in common. You cannot change properties such as the LUA LU name or number, because these values are unique for each LUA LU.  
  
 You can add new IP addresses and subnet masks to a range of LUA LUs. If the new IP address or subnet mask already exists on some of the LUA LUs, but not on others, the addition will occur without duplication in the ones that already have the IP address or subnet mask. You can also modify or delete the IP addresses that the LUA LUs have in common and that appear on the IP address list.  
  
 Configuration changes are apparent only to users who establish a connection after the changes are saved. Users who were connected at the time the configuration changes were made will not be affected.  
  
## See Also  
 [TN3270](../HIS2010/tn32701.md)