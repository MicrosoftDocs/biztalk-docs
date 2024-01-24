---
title: Definition properties for IBM System i
description: Learn more about definition properties for IBM System i.
ms.service: host-integration-server
ms.topic: conceptual
ms.date: 11/28/2023
---

# Definition properties for IBM System i

The following tabs are available on the definition properties for IBM System i:

## IBM System i Definition Properties: General  

| Property | Description |
|----------|-------------|
| **IBM System i Remote LU Alias** | From the list, select **IBM System i Remote LU Alias**, which contains addressing information for the IBM System i. |
| **Local LU Alias** | From the list, select **Local LU Alias**. The **Local LU Alias** maps to the LU the client computer will use. |
| **Mode** | You must select **QPCSUPP mode**. |
| **System 36, AS/36** | Select if you're connecting to a System 36 or AS/36 computer system. |
| **IBM System i User Name** | Enter your **IBM System i User Name**, which is required information. |
| **IBM System i Password** | Enter your **IBM System i Password**, which is required information. |
| **Confirm Password** | Enter your password again to confirm. |
| **Comment** Optionally, enter a comment that's not more than 25 characters long. |
  
## IBM System i Definition Properties: Terminal Types  

**Terminal Names**: Terminal names are displayed. You can remove selection of individual terminal names that don't apply to your network configuration by clearing the checkbox opposite the name.

### Port  
  
### Use Default

To use the port number configured with the service, on the **Service Properties** page, select **Use Default**.

### Use  

TN services listen on multiple ports simultaneously. You can set a default number for the TN service and override this number on a per session basis, allowing a single client computer to connect to multiple host computers.

To override the default value for a given session. select **Use**, and enter another port number.

Configuration changes are apparent only to users who establish a connection after the configuration changes are saved. Users who are connected when configuration changes are made aren't affected.
  
## IBM System i Definition Properties: IP Address List  

You can associate this LUA to a specific IP address or server name. The IP address for an incoming connection is compared to each of the available LUs or pools in turn. Each resource has an associated list of IP address patterns and subnet masks. The IP address from the incoming connection is masked (by bit and by the resource's subnet mask) and is then compared to the resource's IP address pattern masked by the resource's subnet mask. If the result is equal, the connection is allocated to this resource.

| Property | Description |
|----------|-------------|
| **Add Address** | Select to specify the **IP Address** and **Subnet Mask** for the client workstation to where you're granting access. <br><br>**Note**: If you want to assign a specific IP address, you must change the IP address from the default value of 0.0.0.0. If you try to add the default IP address with the default subnet mask value, you will receive a message that indicates an invalid IP address or subnet mask. |
| **IP Address** | To edit the IP address for a client workstation, select an entry in the **IP Address** column. |
| **Subnet Mask** | To edit the subnet mask for a client workstation, select an entry in the **Subnet Mask** column. |
| **Add Name** | Select to add a workstation name to the **IP Address** list box. The workstation name identifies that a client workstation whose address resolves to that name can connect to the service. |
| **Remove** | Select to remove an entry that is currently highlighted in the **IP Address** list box. |
| **Clear All** | Select to remove all entries in the **IP Address** list box. The service is then configured to allow access from any client workstation. |

## See also

[SNA Manager Help](../core/sna-manager-help1.md)
