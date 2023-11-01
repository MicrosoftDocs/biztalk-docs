---
title: Configure an IP-DLC link service
description: Learn how to configure an IP-DLC link service.
ms.prod: host-integration-server
ms.topic: how-to
ms.date: 11/30/2017
---

# Configure an IP-DLC link service

As with other link services, configuration requires that you set parameters in the **Link Service Properties** box. Before you start, read this guide about the configuration process, so that you can gather all the necessary information.

## Configure parameters for an IP-DLC link service  

1. To configure an existing IP-DLC link service, in the MCC snap-in scope pane, open the IP-DLC link service shortcut menu, select **Properties**, which opens the **IP-DLC Link Service Properties** box, and select **Configure**.

   If you just created a new IP-DLC link service, the **IP-DLC Link Service Properties** box opens automatically.

1. Based on the following table, add the required parameters:

   | Property | Description |  
   |----------|--------------|
   | **Service name** | The link service name. For a new link service, the name is predefined as SNAIP#, where # is the ordinal number of the link service. |
   | **Service title** | Enter a user-friendly text description of up to 128 characters. This name appears in the Service Control Manager. The default value is IP-DLC Link Service #N, where N is the ordinal number of the link service. |
   | **Primary NNS** | Enter the IP address, host name, or fully qualified name of the primary network node server. No default value exists. |  
   | **Backup NNS** | Optionally, enter the IP address, host name, or fully qualified name of the backup network node server. No default value exists.|  
   | **No Preferred NNS** | - Selected: This option enables the IP-DLC link service to use the first available network node server. <br><br>- Unselected: The link service always uses the Primary NNS when available. |  
   | **Local address** | This set of parameters assigns the link service to a particular IP address on the local computer. Every link service must be associated with a local IP address or logical connection. Neither the IP address nor the logical connection can be used by another IP-DLC link service on the local computer. |
   | **Adapter address** | When selected, this option forces the link service to use the default IP address associated with the network adapter specified in the adjacent list. The alternative is to associate with a static IP address. The list displays all available network adapters currently configured. Physical adapters are listed first, followed by virtual adapters, that is, WAN Mini-ports. |
   | **Static IP address** | When selected, this option button forces the link service to use the IP address specified in the adjacent list. The list displays all static IP addresses defined to the local computer. Enter the IP address, host name, or fully qualified name for the IP-DLC link service. |
   | **Use IPv6** | Indicates the link service should use IPv6 protocol to communicate with the host. |
   | **Local APPN node** | This set of parameters configures the network identification of the APPN branch network node implemented by the IP-DLC link service.<br /><br /> Note: No other IP-DLC link service within the APPN network can use both the same network name and control point name as this one. You can reuse individual names may be reused, but not the pair. |
   | **Network name** | Enter the APPN network name for the IP-DLC link service operating as a local APPN node across which the IP-DLC link service will communicate. This value must be text with a maximum of eight characters and must comply with the APPN naming convention. No default value exists. |
   | **Control point name** | Enter the APPN control point name for the IP-DLC link service operating as a local APPN node. This value must be text with a maximum of eight characters and must comply with the APPN naming convention. The control point name must be unique for this computer on the APPN network. No default value exists. |  
   | **Use Dynamic PU Definition** | When selected, this option allows the IP-DLC link service to attempt to use the dynamically defined PU definitions on the host. |
   | **Node ID** | In the first box, enter any valid 3-digit hexadecimal number except the reserved numbers of 000 and FFF. In the second box, enter any valid hexadecimal number except the reserved number 00000. No default value exists. |
   | **Associated LEN node** | Select an SNA service operating as an APPN LEN node to associate with this IP-DLC link service. The default value is the first SNA service on the local computer. |

1. To save the settings to the configuration file and registry, select **OK**.

1. In the **Insert Link Service** box that opens, select **Complete Configuration of the IP-DLC Link Service**.

### General configuration options

The **General** page includes specific required key configuration options so that the IP-DLC link service can communicate with the NNS and the APPN network.
  
### Advanced configuration options

The **Advanced** page includes configuration options that control advanced tuning options for the IP-DLC link service. In most cases, use the default setting.
  
| Option | Description |  
|--------|-------------|  
| **IP-DLC Timeouts** | Specify how the IP-DLC link service handles timeouts. |
| **Receive ACK** | Set the duration in milliseconds for the IP-DLC ACK timer. This timeout corresponds to SRQTIME parameter on the IBM host. <br><br>- Default value: 15000 <br>- Limits: 1-65535 |
| **Livetime** | Set the live time duration in milliseconds for LDLC keepalives. This timeout corresponds to LIVTIME parameter on the IBM host. <br><br>- Default value: 10000 <br>- Limits: 1-65535 |  
| **Maximum CMD retransmissions** | Set the maximum number of retransmission attempts for an IP-DLC CMD frame. This timeout corresponds to SRQRETRY parameter on the IBM host. <br><br>- Default value: 3 <br>- Limits: 1–65535 |  
| **Maximum BTU sizeSend** | Set the maximum send Basic Transmission Unit (BTU) size in bytes for IP-DLC. <br><br>- Default value: 1493 <br>- Limits: 768-4096 |
| **Receive** | Set the maximum receive BTU (Basic Transmission Unit) size in bytes for IP-DLC. <br><br>- Default value: 1493 <br>- Limits: 768-4096 |  
| **HPR/IP activation retriesInfinite** | Set infinite retries for HPR/IP link activation. Default value: Unselected |
| **Limited** | Sets the maximum retries for HPR/IP link activation. If this option is selected, the edit box is available. <br><br>- Default value: Selected and the value is set to 10. <br>- Limits: 1–65534 |  
| **Delay between retries** | If this option is selected, set the time between HRP/IP link activation attempts. <br><br>- Default value: 25 <br>- Limits: 1–65534 |  
| **Progressive Mode ARB** | Progressive Mode ARB (Adaptive Rate-Based) enhances Responsive Mode ARB to address potential performance issues that might occur when some systems are implemented in virtualized environments. |  
| **Disable Progressive Mode ARB** | If this option is selected, the IP-DLC link service uses Responsive Mode ARB. Default value: Unselected <br><br>This option should be left at the default value, especially if the Host Integration Server system is running in a virtualized environment. |
| **Delayed Path Switch Timer** | Delay an HPR path switch if an outage is detected on the HPR link. At times, the HPR path switch might occur due to possibly short-lived transient network conditions. If you don't want path switches to occur during transient network conditions, you can use this timer to delay the path switch attempt so that path switches only occur when the outage is more severe. |

### VRN configuration options
  
The **VRN** page includes configuration options that control whether or not the IP-DLC link service uses Virtual Routing Nodes (VRN). These VRN are virtual nodes that exist in an Advanced Peer-to-Peer Networking (APPN) topology database. With APPN nodes that operate in a VRN, you can create dynamic connections to other APPN nodes in the same VRN. VRNs provide the following benefits:

- If direct connectivity between APPN nodes is required, VRNs reduce the number of APPN link definitions that must be manually defined.

- VRNs remove potential bottlenecks that are caused when session traffic is routed through intermediate network nodes (NNs) and when direct APPN links between APPN nodes do not exist.

- Fewer topology database updates (TDUs) are sent across the APPC network when VRNs are used. The number of TDUs is more when you manually define direct APPC link definitions between APPN nodes.
  
The following list describes the options that you can use:

- **VRN**

  To add a Virtual Routing Node Entry, select **Add**.

  - The VRN name consists of two names that are separated by a period (**.**). Each name can be 1 to 8 characters long. The total length of a VRN name cannot exceed 17 characters.
  - You can up to the maximum of 16 VRN names for each IP-DLC link service that's installed on a Host Integration Server.

- **Configure as limited resource**

  To have the IP-DLC link service treat VRN links as limited resources, select this option.

  Limited resource links are automatically deactivated when no traffic flows over the link for a specified time-out period. The default setting causes the IP-DLC link service to treat VRN links as non-limited resources. You must also configure the other end of the VRN link so that the VRN link is treated as a non-limited resource link. If the other end of the VRN link is an IBM mainframe, you should configure LIMRES=NO in Virtual Telecommunications Access Method (VTAM) to enable the link to be treated as a non-limited resource link. If either end of the VRN link treats the link as a limited resource link, the link will be deactivated as soon as the specified aliveness timer expires.

## See also

[Creating and Configuring Connections](../core/creating-and-configuring-connections1.md)
