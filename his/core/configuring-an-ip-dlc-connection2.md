---
title: "Configuring an IP-DLC Connection2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "his_ip_dlc_managing_ip_dlc_link_service_connections_kmdz"
ms.assetid: 4ccd47be-df34-4e22-a748-dc92edbff933
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring an IP-DLC Connection
As with other connections, configuration requires setting parameters on the **Connection** properties dialog box. It is recommended that you read this section before beginning the configuration process, so that you can gather all the necessary information before you start.  
  
#### To configure an IP-DLC connection  
  
1. If you have just created an IP-DLC link service connection, the **Connection** properties dialog box displays. If it does not appear, or if you are configuring an already-existing IP-DLC link service connection, right-click the IP-DLC link service connection in the results pane of the MCC snap-in, and click **Properties**.  
  
2. Add the required parameters according to the tables below.  
  
   **General Page**  
  
   The **General** page is similar to that used for other connections in Microsoft® Host Integration Server.  
  
|||  
|-|-|  
|**Property**|**Comments**|  
|Name|Name of the connection.|  
|Link service|This list displays all currently configured IP-DLC link services.|  
|Comment|Descriptive comment (optional).|  
|Activation|Specifies conditions under which connection is activated.|  
|On server startup|Connection is activated on server startup.|  
|On demand|Connection is activated on demand.|  
|By administrator|Connection can only be activated by system administrator.|  
|Allowed direction|Specifies the connection directions. For more information, see the note under Peer system later in this table.|  
|Outgoing calls|Connection is outgoing.|  
|Incoming calls|Connection is incoming.|  
|Both directions|Connection can be both incoming and outgoing.|  
|Remote end|Specifies which system is the remote end.|  
|Host system|Selecting this option signifies that the connection will be used for Dependent LU Server (DLUS) traffic and may have dependent LUs. You cannot associate independent APPC LUs with an IP-DLC connection remote end type of host system.<br /><br /> For more information about how to configure dependent APPC LUs when using IP-DLC connections, refer to the following KB Article:  [939193](http://support.microsoft.com/default.aspx?scid=kb;EN-US;939193) How to set up the connection and the logical units for an APPC application when you use the IP-DLC link service in Host Integration Server 2006 together with dependent APPC logical units.|  
|Peer system|Selecting this option signifies that the connection will be used for independent APPC LU sessions. You cannot associate dependent 3270 LUs with an IP-DLC connection remote end type of peer system. Because peer system IP-DLC connections do not support DLUS traffic, selecting this option will disable all controls on the **Address** page and the IP-DLC page (shown later in this topic). Only one peer connection can be associated with an IP-DLC link service.<br /><br /> Note: Selecting Peer system automatically sets Activation to **On Server Startup** and Allowed direction to **Both**.|  
  
 **Address Page**  
  
 Use this page to configure DLUS properties for the connection. The DLUS on the mainframe system operates in conjunction with the Dependent LU Requester (DLUR) on the local Host Integration Server computer. Together they route dependent (for example, 3270) sessions across the APPN network using the IP-DLC link service.  
  
 If you selected the Remote end as Peer system on the **General** page, all controls on this page will be disabled.  
  
|||  
|-|-|  
|**Property**|**Comments**|  
|Primary DLUS|Fill in these required fields for the primary server with the appropriate names.|  
|Network name|Represents the APPN network in which to locate the primary DLUS. The network name corresponds to the NETID parameter in VTAM. The network name can contain a maximum of eight characters and can consist of alphanumeric characters and the special characters $, #, and @.  The name must not begin with a digit.|  
|Control point name|Represents the control point name of the primary DLUS. The control point name corresponds to the SSCPNAME parameter in VTAM. The control point name can contain a maximum of eight characters and can consist of alphanumeric characters and the special characters $, #, and @.  The name must not begin with a digit.|  
|Backup DLUS|Fill in these fields for the backup server with the appropriate names. These fields are optional.|  
|Preferred route|Optionally, enter the IP address, host name, or fully qualified name for the NNS as routing server through which to connect to the DLUS. Using a separate NNS may improve host performance by offloading the DLUS host computer from operating as an NNS directory server. The IP-DLC link service will attempt to establish the connection to the DLUS using the preferred route address.|  
  
 **System Identification Page**  
  
 The **System Identification** page is similar to that used for other connections in Host Integration Server.  
  
 If you selected the Remote end as Peer system on the **General** page, all controls on this page will be disabled.  
  
|||  
|-|-|  
|**Property**|**Comments**|  
|Network name|Represents the APPN network where the PU (Physical Unit) is defined.|  
|Control Point Name|Represents the control point name for the PU that the connection represents.|  
|Node ID|Required. Enter a hexadecimal value to uniquely identify the PU for the host connection. This value must match an existing remote LEN-style PU definition. Default value is 05D FFFFF. The node ID value must match the value configured on the host DLUS computer.|  
|Link compression|Optional. Choose a setting from the list. The default value is **None**.|  
  
 **IP-DLC Page**  
  
 Use this page to optionally set parameters specific to the IP-DLC connection.  
  
 If you selected the Remote end as Peer system on the **General** page, all controls on this page will be disabled.  
  
|||  
|-|-|  
|**Property**|**Comments**|  
|Connection retry limits|These settings are used for setting the retry limits when initially activating the connection to the DLUS. In this case, the DLUR (Dependent LU Requester) is the IP-DLC link service.|  
|Unlimited|The IP-DLC link service retries activation of the connection until it is successful.|  
|Limited|Specifies the number of retries, from 1 through 65534. Default value is 8.|  
|Delay after retry|Specifies the wait period between retry attempts. The value of this field can only be configured in 5-second increments with the default value being 10 seconds. This is because the value is saved in the HIS configuration in 5-second units. If you enter a value of 65535 or less (as long as it is a multiple of 5), the value entered will be used. If the value is not a multiple of 5 when you save your changes, a dialog box appears indicating that the value is not a multiple of 5 and that it has been rounded. If you enter a value larger than 65535, the value will be changed to an unexpected value. For example: If a value of 70000 is manually entered, a value of 4464 displays when you click the **Apply** button.|  
|DLUR retry limits|Optional. Use these controls to specify retry action in case the DLUR connection fails. Default setting is Limited.|  
|No retries|No retry attempts are made.|  
|Unlimited|The IP-DLC link service retries activation until it is successful.|  
|Limited|Specifies the number of retries, from 1 through 65534. Default value is 8.|  
|Delay after retry|Specifies the wait period after each retry, from 1 through 65535 seconds. Default value is 10 seconds.|  
  
## See Also  
 [Creating and Configuring Link Services](../core/creating-and-configuring-link-services2.md)