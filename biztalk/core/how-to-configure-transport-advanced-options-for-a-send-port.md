---
description: "Learn more about: Configure Transport Advanced Options for a Send Port"
title: "How to Configure Transport Advanced Options for a Send Port"
ms.custom: "biztalk-2020"
ms.date: "01/13/2020"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Configure Transport Advanced Options for a Send Port

Use the BizTalk Server Administration console to configure transport advanced options for a send port. These options determine how messages are handled by the send port, such as the number of times to retry sending messages on message failure and the service window schedule for the port.  

- **Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can enable ordered delivery for dynamic send ports, depending on the adapter type. This option is only available for the adapter types where ordered delivery is guaranteed for static send ports, such as the File adapter, or the FTP adapter.

  Consider six messages: M1, M2, M3, M4, M5, and M6. M1, M3, M5 are meant for a file location. M2, M4, and M6 are meant for FTP. The ordered delivery dynamic send port makes sure that M1, M3, and M5 are ordered; and M2, M4, and M6 are ordered respectively. 

  For those adapter types that don't support ordered delivery, there aren't any dynamic send port properties available to configure. Their transport options are automatically determined at run time.  

- **For previous BizTalk versions** that use dynamic ports, there aren't any properties available to configure because the transport options are automatically determined at run time.
  
- **Starting with BizTalk Server 2020**, dynamic send ports with ordered delivery can process messages to different outbound locations in parallel, allowing for higher throughput. Order will be maintained per unique outbound location, but not across different outbound locations even for the same transport type.

  Consider six messages: M1, M2, M3, M4, M5, and M6. M1, M3, M5 are meant for a file location F1. M2, M4, and M6 are meant for a file location F2. The ordered delivery dynamic send port makes sure that M1, M3, and M5 are ordered; and M2, M4, and M6 are ordered respectively.

  You can choose to enforce order across all outbound locations for a given transport type by changing the **Enforce order across outbound locations** setting on the **Transport Advanced Options** tab. Consider the six messages scenario above. If **Enforce order across outbound locations** is enabled, the port will ensure that all six message M1, M2, M3, M4, M5, M6 are delivered in order. 

## Prerequisites

To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## Controlling Send Port Priority

The Priority setting of the Transport Advanced Options controls the order in which messages are removed from the message box. Ports with a higher priority will be processed earlier than ports with a lower priority making the higher priority ports more important relative to other send ports within a single host.  
  
Priority is useful in scenarios requiring low response times for certain types of requests. For example, if there are multiple send ports that connect to different systems for processing normal requests and interactive requests. The interactive requests require a low response time, so when an interactive request is submitted, you want to ensure it is processed as soon as possible.  
  
BizTalk Server does not attempt to be fair in the processing of messages with different priorities in the message box. If there are equal numbers of items with two different priorities in the message box when processing begins, the lower priority items will be processed only after all high priority items have been processed. If the volume of high priority items is great, it is possible that items with a lower priority will never be processed. In other words, the lower priority items will experience starvation.  
  
> [!WARNING]
> To minimize the risk of message starvation, thoroughly test your application under realistic loads to ensure all messages are processed. Failure to test your solution may result in unprocessed messages.  
  
 Internally, BizTalk Server assigns a priority to every subscription. Priority can be any number from 1 (highest priority) to 10 (lowest priority). Because the default priority is 7 for activating subscriptions and 5 for correlating subscriptions, correlating messages will be delivered earlier than activating subscriptions.  
  
## Configure the transport options 
  
1.  Open **BizTalk Server Administration**.  
  
2.  Expand the BizTalk group, and then expand your BizTalk application.  
  
3.  Select **Send Ports**, right-click the send port to configure, and then select **Properties**.  
  
4.  In the left pane, select **Transport Advanced Options**.  
  
5.  Configure the transport options as described in the following table, and then select **OK**.  Only some of the following properties are available for dynamic send ports.
  
    - **Retry count**: Enter the number of times for the send port to resend a message on message failure. The default is 3; the allowed range is from 0 through 1,000.
    - **Retry interval**: Enter the interval in minutes between message resend attempts. The default is 5; the allowed range is from 0 through 525,600.
    - **Priority**: Set the priority of the resend attempt.
    - **Ordered delivery**: Select this check box to send messages in order of receipt.
    - **Stop sending subsequent messages on current message failure**: Select this check box to stop sending subsequent messages that follow a failed message. This option is available only when the **Ordered delivery** option is selected.
    - **Enforce order across outbound locations**: This property is only visible for dynamic send ports. Select this check box to enforce ordered delivery across all outbound locations for a given transport type. This option is available only when the **Ordered delivery** option is selected.

      This setting applies to:

      - BizTalk Server 2020 and newer

    - **Enable routing for failed messages**: Select this option to enable routing for failed messages. 
    - **Enable service window**: Select this option to specify the time period each day during which the send port will be operational by specifying a start time and stop time.
    - **Start time**: Enter the time each day at which the send port starts sending messages. This option is available only when the **Enable service window** option is selected.
    - **Stop time**: Enter the time each day at which the send port stops sending messages. This option is available only when the **Enable service window** option is selected.
  
## See Also

[Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md)  
[Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)
