---
title: "AS-400 Definition Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_AS400TN"
ms.assetid: ccb6fc38-ca11-4089-b085-a7eef713585c
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# AS/400 Definition Properties
The following tabs are available on the AS/400 Definition Properties:  
  
## AS/400 Definition Properties: General  
 **AS/400 Remote LU Alias**  
 Click the drop-down list box arrow and select an **AS/400 Remote LU Alias**, which contains addressing information for the AS/400.  
  
 **Local LU Alias**  
 Click the drop-down list box arrow and select a **Local LU Alias**. The **Local LU Alias** maps to the LU the client computer will use.  
  
 **Mode**  
 You must select the **QPCSUPP mode**.  
  
 **System 36, AS/36**  
 Select if connection to a System 36 or AS/36 computer system.  
  
 **AS/400 User Name**  
 Enter your **AS/400 User Name**, which is required information.  
  
 **AS/400 Password**  
 Enter your **AS/400 Password**, which is required information.  
  
 **Confirm Password**  
 Enter your password again to confirm.  
  
 **Comment**  
 Optionally, enter a comment of not more than 25 characters long.  
  
## AS/400 Definition Properties: Terminal Types  
 **Terminal Names**  
 Terminal names are displayed. You can remove selection of individual terminal names that do not apply to your network configuration by clearing the checkbox opposite the name  
  
### Port  
  
### Use Default  
 Select **Use Default** to use the port number configured with the service (on the Service Properties page).  
  
### Use  
 You can override the default value for a given session by selecting **Use** and typing another port number.  
  
> [!NOTE]
>  TN services listen on multiple ports simultaneously. You can set a default number for the TN service and override this number on a per session basis, allowing a single client computer to connect to multiple host computers.  
  
> [!NOTE]
>  Configuration changes are apparent only to users who establish a connection after the configuration changes are saved. Users who were connected at the time the configuration changes were made will not be affected.  
  
## AS/400 Definition Properties: IP Address List  
 You can associate this LUA to a specific IP address or server name.  
  
 **Add Address**  
 Click to specify the **IP Address** and **Subnet Mask** of the client workstation to which you are granting access.  
  
 **IP Address**  
 Click an entry in the **IP Address** column to edit the IP address for a client workstation.  
  
 **Subnet Mask**  
 Click an entry in the **Subnet Mask** column to edit the subnet mask for a client workstation.  
  
 **Add Name**  
 Click to add a workstation name to the **IP Address** list box. The workstation name identifies that a client workstation whose address resolves to that name can connect to the service.  
  
 **Remove**  
 Click to remove an entry that is currently highlighted in the **IP Address** list box.  
  
 **Clear All**  
 Click to remove all entries in the **IP Address** list box. The service will then be configured to allow access from any client workstation.  
  
> [!NOTE]
>  The IP address must be changed from the default value of 0.0.0.0 if you want to assign a specific IP address. If you try to add the default IP address with the default subnet mask value, you will receive a message indicating an Invalid IP Address/Subnet Mask.  
  
> [!NOTE]
>  The IP address of an incoming connection is compared to each of the available LUs or pools in turn. Each resource has an associated list of IP address patterns and subnet masks. The IP address from the incoming connection is masked (by bit and by the resource's subnet mask), then compared to the resource's IP address pattern masked by the resource's subnet mask. If the result is equal, the connection is allocated to this resource.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)