---
title: "Configuring an IP-DLC Link Service1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efe4f455-2a08-4d90-bffb-544285927376
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring an IP-DLC Link Service
As with other link services, configuration requires setting parameters on the **Link Service Properties** dialog box. It is recommended that you read this section before beginning the configuration process, so that you can gather all the necessary information before you start.  
  
#### To configure an IP-DLC link service  
  
1. If you have just created a new IP-DLC link service, the **IP-DLC Link Service Properties** dialog box displays. To reconfigure an existing IP-DLC link service, right-click the IP-DLC link service in the scope pane of the MCC snap-in, click **Properties**, and then click the **Configure** button to load the IP-DLC Link Service Properties dialog box.  
  
2. Add the required parameters according to the following table.  
  
3. Click **OK** to persist the settings to the configuration file and registry. The **Insert Link Service** dialog box appears.  
  
4. Click **Complete Configuration of the IP-DLC Link Service**.  
  
   **General**  
  
   The **General** page includes specified key configuration options that are required so that the IP-DLC link service is able to communicate with the NNS and the APPN network.  
  
|||  
|-|-|  
|**Property**|**Comments**|  
|Service name|Displays the name of the link service being configured. For a new link service, the name is predefined as SNAIP#, where # is the ordinal number of the link service.|  
|Service title|Enter a user-friendly text description of up to 128 characters. This name appears in the Service Control Manager. The default value is IP-DLC Link Service #N, where N is the ordinal number of the link service.|  
|Primary NNS|Enter the IP address, host name, or fully qualified name of the primary network node server. There is no default value.|  
|Backup NNS|Optionally, enter the IP address, host name, or fully qualified name of the backup network node server. There is no default value.|  
|No Preferred NNS|Selecting this option enables the IP-DLC link service to use the first available network node server. If this option is not selected, the link service will always use the Primary NNS when it becomes available.|  
|Local address|This set of parameters assigns the link service to a particular IP address on the local computer. Every link service must be associated with a local IP address or logical connection, and neither the IP address nor the logical connection can be used by another IP-DLC link service on the local computer.|  
|Adapter address|Selecting this option button forces the link service to use the default IP address associated with the network adapter specified in the adjacent list. (The alternative is to associate with a static IP address.) The list displays all available network adapters currently configured. Physical adapters are listed first, followed by virtual adapters (that is, WAN Mini-ports).|  
|Static IP address|Selecting this option button forces the link service to use the IP address specified in the adjacent list. The list displays all static IP addresses defined to the local computer. Enter the IP address, host name, or fully qualified name for the IP-DLC link service.|  
|Use IPv6|Indicates the link service should use IPv6 protocol to communicate with the host.|  
|Local APPN node|This set of parameters configures the network identification of the APPN branch network node implemented by the IP-DLC link service.<br /><br /> Note: No other IP-DLC link service within the APPN network can use both the same network name and control point name as this one. Individual names may be reused, but the pair may not.|  
|Network name|Enter the APPN network name for the IP-DLC link service operating as a local APPN node across which the IP-DLC link service will communicate. This value must be text with a maximum of eight characters and must comply with the APPN naming convention. There is no default value.|  
|Control point name|Enter the APPN control point name for the IP-DLC link service operating as a local APPN node. This value must be text with a maximum of eight characters and must comply with the APPN naming convention. There is no default value. The control point name must be unique for this computer on the APPN network.|  
|Use Dynamic PU Definition|Selecting this option allows the IP-DLC link service to attempt to use the dynamically defined PU definitions on the host.|  
|Node ID|In the first box, enter any valid 3-digit hexadecimal number except the reserved numbers of 000 and FFF. In the second box, enter any valid hexadecimal number except the reserved number 00000. There is no default value.|  
|Associated LEN node|Select an SNA service operating as an APPN LEN node to associate with this IP-DLC link service. The default value is the first SNA service on the local computer.|  
  
 **Advanced Page**  
  
 The **Advanced** page includes configuration options that control advanced tuning options for the IP-DLC link service. In most cases, the default setting should be used.  
  
|**Option**|**Comment**|  
|----------------|-----------------|  
|IP-DLC Timeouts|These settings specify how the IP-DLC link service handles timeouts.|  
|Receive ACK|You can select this option to set the duration of the IP-DLC ACK timer in milliseconds. This timeout corresponds to SRQTIME parameter on the IBM host.<br /><br /> Default value: 15000 Limits: 1-65535|  
|Livetime|You can select this option to set the duration of the live time for LDLC keepalives in milliseconds. This timeout corresponds to LIVTIME parameter on the IBM host.<br /><br /> Default value: 10000 Limits: 1-65535|  
|Maximum CMD retransmissions|You can select this option to set the maximum number of retransmission attempts for an IP-DLC CMD frame. This timeout corresponds to SRQRETRY parameter on the IBM host.<br /><br /> Default value: 3 Limits: 1 – 65535|  
|Maximum BTU sizeSend|You can select this option to set the maximum send BTU (Basic Transmission Unit) size in bytes for IP-DLC.<br /><br /> Default value: 1493 Limits: 768-4096|  
|Receive|You can select this option to set the maximum receive BTU (Basic Transmission Unit) size in bytes for IP-DLC.<br /><br /> Default value: 1493 Limits: 768-4096|  
|HPR/IP activation retriesInfinite|You can select this option to set infinite retries for HPR/IP link activation.<br /><br /> Default value: unchecked|  
|Limited|The edit box is enabled when the option button is selected. The edit control sets the maximum retries for HPR/IP link activation.<br /><br /> Default value: radio button is checked, edit box has value of 10 Limits: 1 – 65534|  
|Delay between retries|You can select this option to set the time between HRP/IP link activation attempts.<br /><br /> Default value: 25 Limits: 1 – 65534|  
|Progressive Mode ARB|Progressive Mode ARB (Adaptive Rate-Based) is an enhancement to Responsive Mode ARB to address potential performance issues that could occur when some systems are implemented in virtualized environments.|  
|Disable Progressive Mode ARB|If you select this option, the IP-DLC link service will use Responsive Mode ARB. This option is unchecked by default. This option should be left at the default value, especially if the Host Integration Server system is running in a virtualized environment.|  
|Delayed Path Switch Timer|You can select this option to delay an HPR path switch if an outage has been detected on the HPR link. At times the HPR path switch may occur due to transient network conditions that may be short-lived. If you do not want path switches to occur during transient network conditions, you can use this timer to delay the path switch attempt so that path switches only occur when the outage is more severe.|  
  
 **VRN Page**  
  
 The **VRN** page includes configuration options that control whether or not Virtual Routing Nodes will be used by the IP-DLC link service.  
  
 Virtual Routing Nodes (VRN) are virtual nodes that exist in an Advanced Peer-to-Peer Networking (APPN) topology database. APPN nodes that operate in a VRN enable you to create dynamic connections to other APPN nodes in the same VRN. VRNs provide the following benefits:  
  
- If direct connectivity between APPN nodes is required, VRNs reduce the number of APPN link definitions that must be manually defined.  
  
- VRNs remove potential bottlenecks that are caused when session traffic is routed through intermediate network nodes (NNs) and when direct APPN links between APPN nodes do not exist.  
  
- Fewer topology database updates (TDUs) are sent across the APPC network when VRNs are used. The number of TDUs is more when you manually define direct APPC link definitions between APPN nodes.  
  
  The following table lists the options that you can use:  
  
|**Option**|**Comment**|  
|----------------|-----------------|  
|VRN|Click Add to add a Virtual Routing Node Entry. The VRN name consists of two names that are separated by a period (.). Each name can be 1 to 8 characters long. The total length of a VRN name cannot exceed 17 characters. A maximum of 16 VRN names can be added for each IP-DLC link service that is installed on a Host Integration Server.|  
|Configure as limited resource|If this option is checked, the IP-DLC link service will treat VRN links as limited resources. Limited resource links are automatically deactivated when no traffic flows over the link for a specified time-out period. The default setting causes the IP-DLC link service to treat VRN links as non-limited resources.<br /><br /> In addition, the other end of the VRN link must also be configured so that the VRN link is treated as a non-limited resource link. If the other end of the VRN link is an IBM mainframe, you should configure LIMRES=NO in Virtual Telecommunications Access Method (VTAM) to enable the link to be treated as a non-limited resource link. If either end of the VRN link treats the link as a limited resource link, the link will be deactivated as soon as the specified aliveness timer expires.<br /><br /> Note: The default behavior in all versions of Host Integration Server prior to Host Integration Server was to treat VRN links as limited resources. An update was provided for Host Integration Server 2006 SP1 and Host Integration Server 2009 to allow VRN links to be treated as non-limited resources so that they were not deactivated when the links were idle.|  
  
## See Also  
 [Creating and Configuring Connections](../core/creating-and-configuring-connections1.md)