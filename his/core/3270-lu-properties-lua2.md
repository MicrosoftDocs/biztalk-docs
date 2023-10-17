---
description: "Learn more about: 3270 LU Properties: LUA"
title: "3270 LU Properties: LUA2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_LU_LUa"
ms.assetid: 54eb9f43-1333-446f-8c37-e7cae04af188
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# 3270 LU Properties: LUA
The following tabs are available on the 3270 LUA Properties Sheet:  
  
## 3270 LU Properties: LUA General Tab  
 **LU Number**  
  **Enter the LU Number for LUs on 802.2, SDLC, or X.25.**  
 Enter an appropriate LU Number.  
  
 **LU Name**  
 Type the LU Name.  
  
 **Connection**  
 The connection for this LU is shown. The connection cannot be changed from this dialog box.  
  
 **Pool**  
 If the LU has already been assigned to a pool, the pool name appears here.  
  
 **Comment**  
 Optionally, enter a comment of not more than 25 characters.  
  
 **Use Compression**  
 Select this option to enable 3270 LU data stream compression. This option must also be set in the host VTAM configuration for the LU.  
  
 **User Workstation Secured**  
 Select this option to enable a higher level of security. When the option is selected the user can only acquire an LU if:  
  
 the user's User Record is assigned to this LU, and  
  
 the user's workstation has been defined with a Workstation Definition.  
  
 **High Priority Mode**  
 Select this option to increase the priority for this LU.  
  
> [!NOTE]
>  Two additional property pages appear when the LU is assigned to a TN3270. These are the TN3270 property page and the IP Address List page.  
  
## 3270 LU Properties: TN3270 Tab  
 **Type**  
 Select from the list the display or printer type.  
  
 **Generic Display**  
  
 This is the default pool type. The display LU or pool will be assigned to a client computer that either does not specify a particular LU or Pool, or that requests this LU or Pool by name.  
  
 **Specific Display**  
  
 The LU or pool configured as specific will only be assigned to client systems that request this LU or pool, and not to clients making generic requests.  
  
 **Generic Printer**  
  
 The printer LU or pool will be assigned to a client computer that either does not specify a particular LU or pool, or that requests this LU or pool by name. When this option is checked, the **terminal name** will default to IBM-3287-1.  
  
 **Specific Printer**  
  
 The printer LU or pool configured as specific will only be assigned to client computers that request this LU or pool, and not to client computers making generic requests. When this option is checked, the **terminal name** will default to IBM-3287-1.  
  
 **Associated Printer**  
  
 Printer LUs can be marked as associated instead of generic or specific. To associate a printer LU with a terminal LU, select this option and choose the **Associated LU** from the drop-down list box. When this option is checked, the **terminal name** will default to IBM-3287-1.  
  
 **Sessions**  
 This is the number of TN3270 sessions allowed for the selected LU or pool. The number of TN3270 sessions must not exceed the number of LUs listed under [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Resource Information.  
  
 If you reduce the TN3270 Sessions limit to 0 (zero) TN3270 service will not assign the LU or pool.  
  
 **Associated Printer**  
 When the **Type** option **Associated Printer** is selected, choose an **Associated Printer** from the drop-down list. In this case, the printer LU is partnered with one terminal LU. A client computer accesses that printer LU by sending in an "associate" request and giving the name of the terminal LU with which the printer LU is partnered.  
  
 **Terminal types**  
 TN3270 service will default to IBM Terminal Model 2. To add a different terminal model to this LU, click the corresponding number (**2**, **3**, **4**, or **5**) to the left of the list of terminal names. After a Terminal Model is selected, Terminal Names are automatically assigned. You can remove selection of individual terminal names that do not apply to your network configuration by clearing the checkbox opposite the name, or you can clear all terminal names by clicking **Clear**.  
  
> [!NOTE]
>  The terminal name strings selected must be compatible with the host logmode entry for the LU. For printer LUs, the **Terminal Name** will default to IBM-3287-1.  
  
 **Port**  
 Select **Default port** to use the port number configured with the service (on the Service Properties page), or select a port from the list. The list displays all of the defined TN3270 ports along with their Security setting (High, Medium, Low, None, or Unsecured).  
  
> [!NOTE]
>  TN services listen on multiple ports simultaneously. You can set a default number for the TN service and override this number on a per session basis, allowing a single client computer to connect to multiple host computers.  
  
> [!NOTE]
>  TN3270 client systems can only access LUs that are configured as generic terminal LUs. TN3270 client systems can access generic, specific, and associated LUs.  
  
> [!NOTE]
>  Configuration changes are apparent only to users who establish a connection after the configuration changes are saved. Users who were connected at the time the configuration changes were made will not be affected.  
  
## 3270 LU Properties: IP Address List  
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
