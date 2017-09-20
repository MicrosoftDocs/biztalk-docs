---
title: "SB-Messaging Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c06c4934-45b2-4f6f-9d19-3ebd937c32ae
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SB-Messaging Adapter
The Service Bus (**SB-Messaging**) adapter is used to receive and send from Service Bus entities like Queues, Topics, and Relays. You can use the **SB-Messaging** adapters to bridge the connectivity between [!INCLUDE[winazure](../includes/winazure-md.md)] and on-premises [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], thereby enabling users to create a typical hybrid application. The topics in this section provide instructions on how to configure an **SB-Messaging** receive location and a send port to receive and send messages from the Service Bus entities.  

## Before you get started
Service Bus provides two methods to authenticate: Access Control Service (ACS) and the Shared Access Signature (SAS). Our recommendation is to use Shared Access Signature (SAS) when authenticating with Service Bus. The Shared Access Key value is listed in the [Azure portal](https://portal.azure.com).

When you create a Service Bus namespace, the Access Control (ACS) namespace is not automatically created. To use Access Control, you need the Issuer Name and Issuer Key values of this namespace. These values are available when you create a new ACS namespace using Windows PowerShell. These values are not listed in the Azure portal.

To use ACS for authentication, and get the Issuer Name and Issuer Key values, the overall steps include:

1. Install the [Azure Powershell cmdlets](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).
2. Add your Azure account: `Add-AzureAccount`
3. Return your subscription name: `get-azuresubscription`
4. Select your subscription: `select-azuresubscription <name of your subscription>` 
5. Create a new namespace: `new-azuresbnamespace <name for the service bus> "Location" -CreateACSNamespace $true -NamespaceType Messaging`

    Example:
      `new-azuresbnamespace biztalksbnamespace "South Central US" -CreateACSNamespace $true -NamespaceType Messaging`
      
5. When the new ACS namespace is created (which can take several minutes), the IssuerName and IssuerKey values are listed in the connection string: 

    ```
    Name                  : biztalksbnamespace
    Region                : South Central US
    DefaultKey            : abcdefghijklmnopqrstuvwxyz
    Status                : Active
    CreatedAt             : 10/18/2016 9:36:30 PM
    AcsManagementEndpoint : https://biztalksbnamespace-sb.accesscontrol.windows.net/
    ServiceBusEndpoint    : https://biztalksbnamespace.servicebus.windows.net/
    ConnectionString      : Endpoint=sb://biztalksbnamespace.servicebus.windows.net/;SharedSecretIssuer=owner;SharedSecretValue=abcdefghijklmnopqrstuvwxyz
    NamespaceType         : Messaging
    ```
[New-AzureSBNamespace](https://msdn.microsoft.com/library/dn495165.aspx)

## Receive messages from Service Bus
  
This section provides information on how to configure an **SB-Messaging** Receive Location using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
> [!NOTE]
>  Before completing the following procedure, you must have already added a one-way receive port. See [How to create a receive port](../core/how-to-create-a-receive-port.md).  

 
1.  In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, and then expand the application under you want to create a receive location.  
  
2.  In the left pane, click the **Receive Ports** node and in the right pane, right-click the receive port with which you want to associate the new receive location, and then click **Properties**.  
  
3.  In the left pane of the **Receive Port Properties** dialog box, select **Receive Locations**, and in the right pane click **New** to create a new receive location.  
  
4.  In the **Receive Location Properties** dialog box, in the **Transport** section, select **SB-Messaging** from the **Type** drop-down list, and then click **Configure** to configure the transport properties for the receive location.  
  
5.  In the **SB-Messaging Transport Properties** dialog box, in the **General** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Queue or Subscription URL**|Specify the URL where the Service Bus queue is deployed. Typically the URL is in the following format:<br /><br /> `sb://<namespace>.servicebus.windows.net/<queue_name>`|  
    |**Open Timeout**|Specifies a time span value that indicates the time for a channel open operation to complete.<br /><br /> **Default value:** 1 minute|  
    |**Close Timeout**|Specifies a time span value that indicates the time for a channel close operation to complete.<br /><br /> **Default value:** 1 minute|  
    |**Receive timeout**|Specifies a time span value that indicates the time for a receive operation to complete.<br /><br /> **Default value:** 10 minutes|  
    |**Prefetch count**|Specifies the number of messages that are received simultaneously from the Service Bus Queue or a topic. Prefetching enables the queue or subscription client to load additional messages from the service when it performs a receive operation. The client stores these messages in a local cache. The size of the cache is determined by the value for the Prefetch Count property you specify here.<br /><br /> For more information, refer to the section “Prefetching” at [https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements/](https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements/)<br /><br /> **Default value:** -1|  
    |**Use Session**|Select this check box to use a Service Bus session to receive messages from a queue or a subscription.|  
  
6.  In the **Authentication** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Access Control Service**|Select this to use ACS for authentication and provide the following values:<br /><br /> - Enter the Service Bus Access Control Service STS URI. Typically the URI is in the following format:<br /><br /> `https://<namespace>-sb.accesscontrol.windows.net/`<br /><br /> - Enter the issuer name for the Service Bus namespace.<br /><br /> - Enter the issuer key for the Service Bus namespace.|  
    |**Shared Access Signature** (new starting with [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)])|Select this to use Shared Access Signature (SAS) for authentication, and provide the SAS key name and key value.|  
  
7.  In the **Properties** tab, in the **Namespace for Brokered Message Properties** field, specify the namespace that the adapter uses to write the brokered message properties as message context properties on the message received by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Additionally, if you want to promote the brokered message properties, select the **Promote Brokered Message Properties** check box.  
  
8.  Click **OK**.  
  
9. Enter the appropriate values in the **Receive Location Properties** dialog box to complete the configuration of the receive location and click **OK** to save settings. For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  
  
## Send messages to Service Bus
This section provides information on how to configure an **SB-Messaging** send port using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
1.  In the BizTalk Server Administration console, create a new send port or double-click an existing send port to modify it. For more information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options and specify **SB-Messaging** for the **Type** option in the **Transport** section of the **General** tab.  
  
2.  On the **General** tab, in the **Transport** section, click the **Configure** button.  
  
3.  In the **SB-Messaging Transport Properties** dialog box, on the **General** tab, specify the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Destination URL**|Enter the URL where the Service Bus queue is deployed. Typically the URL is in the following format:<br /><br /> `sb://<namespace>.servicebus.windows.net/<queue_name>`|  
    |**Batch Flush Interval**|Specifies a time span value that indicates the interval when the message batches being sent to a Queue or a Topic are flushed. The default value is 20 milliseconds.<br /><br /> For more information about batching with respect to Service Bus Queues and Topics, see the **Client-side batching** section at [https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements](https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements).|  
    |**Open Timeout**|Specifies a time span value that indicates the time for a channel open operation to complete.<br /><br /> **Default value:** 1 minute|  
    |**Send Timeout**|Specifies a time span value that indicates the time for a send operation to complete.<br /><br /> **Default value:** 1 minute|  
    |**Close Timeout**|Specifies a time span value that indicates the time for a channel close operation to complete.<br /><br /> **Default value:** 1 minute|  
  
4.  In the **Authentication** tab, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Access Control Service**|Select this to use ACS for authentication and provide the following values:<br /><br /> - Enter the Service Bus Access Control Service STS URI. Typically the URI is in the following format:<br /><br /> `https://<namespace>-sb.accesscontrol.windows.net/`<br /><br /> - Enter the issuer name for the Service Bus namespace.<br /><br /> - Enter the issuer key for the Service Bus namespace.|  
    |**Shared Access Signature** (new starting with [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)])|Select this to use Shared Access Signature (SAS) for authentication, and provide the SAS key name and key value.|  
  
5.  In the **Properties** tab, in the **Namespace for the user defined Brokered Message Properties** field, specify the namespace that contains the BizTalk message context properties that you want to write as user-defined Brokered Message properties on the outgoing message sent to the Service Bus Queue. All the properties that belong to the namespace are written to the message as user-defined Brokered Message properties. The adapter ignores the namespace while writing the properties as Brokered Message properties. It uses the namespace only to ascertain what properties to write.  
  
     You can also specify the values for the BrokeredMessage properties. For more information about the properties, see [BrokeredMessage Properties](https://msdn.microsoft.com/library/azure/microsoft.servicebus.messaging.brokeredmessage_properties.aspx).  
  
6.  Click **OK** and **OK** again to save settings.  
  
## See also
[Using adapters](../core/using-adapters.md)