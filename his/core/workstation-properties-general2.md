---
description: "Learn more about: Workstation Properties: General"
title: "Workstation Properties: General2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_Workstation"
  - "SNA_Folder_Workstation"
---
# Workstation Properties: General
**Workstation ID**  
 The **workstation ID** is usually the workstation name.  
  
 **Workstation ID Type**  
 Click the type of workstation ID:  
  
 **Name** is the workstation name.  
  
 **Address** is the IP address. An IP Address specifies one server for a network address.  
  
 **IP Subnet** is the IP Subnet address. An IP Subnet address specifies several servers with the same network address. Subnetting enables host administrators to distribute the hostids for a given netid to several subnets. Without subnetting, an IP address is interpreted in two parts: netid + hostid (network + node). With subnetting, an IP address is interpreted in three parts: netid + subnetid + hostid (network + subnetwork + node). Subnetting is a mechanism for using some bits in the hostid as a subnetid.  
  
 **IP Mask**  
 If you select **IP Subnet**, you must specify the **IP Mask** as well. The IP Mask refers to the netid + subnetid. You must know the IP Mask. For example, an IP Mask might be: "255.255.248.0."  
  
 **Comment**  
 Optionally, enter a comment of no more than 25 characters.  
  
 **Allow access to both workstation and user resources**  
 Select this option to allow users logged on to this computer to see the LUs assigned both to the workstation and to that user.  
  
 **Allow access to workstation resources only**  
 Selecting this option provides a higher degree of security by restricting resources available on this computer to the LUs assigned to this workstation. Users will not be able to access LUs assigned to them unless the LU is also assigned to the workstation. This feature will be useful for secure workstations, such as those used to print checks.  
  
 **Allow access to Dynamically Created Remote APPC LUs**  
 Select this check box to allow users access to remote APPC LU as they are created.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)
