---
description: "Learn more about: How to Configure a POP3 Receive Location"
title: "How to Configure a POP3 Receive Location"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure a POP3 Receive Location
You can set POP3 receive location adapter variables in the BizTalk Server Administration console. If properties are not set in the receive location, the default receive handler values set in the BizTalk Server Administration console are used.  
  
> [!NOTE]
>  Before completing the following procedure you must have already added a receive port. For more information, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  
  
 **To configure variables for a POP3 receive location**  
  
1.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application you want to create a receive location in.  
  
2.  In the BizTalk Server Administration console, in the left pane, click the **Receive Port** node. Then in the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.  
  
3.  In the **Receive Port Properties** dialog box, in the left pane, select **Receive Locations**, and then in the right pane, double-click an existing receive location or click **New**to create a new receive location.  
  
4.  In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **POP3** from the drop-down list, and then click **Configure**.  
  
5.  In the **POP3 Transport Properties** dialog box, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Apply MIME Decoding**|Specify whether to apply MIME decoding to messages received by the POP3 adapter. MIME decoding is used to parse the incoming message and any attachments into a multipart BizTalk message. **Important:**  If this value is set to `False` then the POP3 adapter will submit the complete e-mail body including message headers to BizTalk Server. <br /><br /> Default value: `True`|  
    |**Body Part Content Type**|Specify the body part content type of the incoming e-mail message to submit to BizTalk Server. This is an optional setting. See [What Is the POP3 Adapter?](../core/what-is-the-pop3-adapter.md) for more information.|  
    |**Body Part Index**|Specify the body part of the incoming e-mail message to submit to BizTalk Server. See [What Is the POP3 Adapter?](../core/what-is-the-pop3-adapter.md) for more information.<br /><br /> Default value: 0|  
    |**Mail Server**|Specify the POP3 mail server that houses the mailbox that will be polled by the POP3 adapter. **Note:**  The URI for a send port or receive location cannot exceed 256 characters.|  
    |**Port**|Specify the port for the POP3 mail server.<br /><br /> Valid values: 1 through 65535 inclusive.<br /><br /> Default value: 0 **Note:**  A value of 0 indicates to use the default POP3 port of 110 if **Use SSL** is `False` or port 995 if **Use SSL** is `True`.|  
    |**Authentication Scheme**|Specify the type of authentication to use with the destination server.<br /><br /> Valid options are:<br /><br /> -   **Basic**<br />-   **Digest**<br />-   **SPA** **Note:**  When using SPA authentication, the username must be specified with one of the following formats: Domain accounts must be entered with the syntax: \<domain name\>\\<username\> Local accounts must be entered with the syntax: \<machine name\>\\<username\>|  
    |**Password**|Specify the user password to use for authentication with the POP3 server.|  
    |**Use SSL**|Specify whether to use Secure Sockets Layer (SSL) to communicate with the destination server.<br /><br /> Default value: `False`|  
    |**User Name**|Specify the user name to use for authentication with the POP3 server. This property requires a value. **Note:**  The account specified for the User Name property must have the ability to logon to the network. The POP3 adapter connects to the mailbox associated with the account specified for the User Name property. Therefore it is not possible to use the POP3 Adapter to connect to a mailbox other than the mailbox assigned to the specified account. For example, even if multiple accounts have Read permissions to the mailbox associated with a particular account, only the actual account name can be specified for User Name.|  
    |**Error Threshold**|Specify the maximum number of network or protocol errors to wait before shutting down the adapter. Specify a value of 0 to prevent the adapter from shutting down.<br /><br /> Default value: 10|  
    |**Polling Interval**|Specify the interval between attempts to retrieve messages from the POP3 server.<br /><br /> Default value: 5|  
    |**Polling Interval Unit**|Specify the unit of measure to be used for the **Polling Interval**.<br /><br /> Default value: Minutes|  
  
6.  Click **OK**.  
  
7.  In the **Receive Location Properties** dialog box, enter the appropriate values to complete the configuration of the receive location, and then click **OK** to save settings. For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  
  
> [!NOTE]
>  The POP3 adapter will generate an error and fail to process any messages if the mailbox that it is configured to read from contains more than 2,147,483,647 e-mail messages. The POP3 adapter stores the message count for the mailbox that it is configured to read into an Int32 variable and the maximum value for the Int32 data type is 2,147,483,647.  
  
> [!IMPORTANT]
>  After the POP3 adapter has successfully retrieved an e-mail from a target mailbox it deletes the e-mail from the mailbox. This behavior is by design to help prevent the POP3 adapter from retrieving multiple copies of an e-mail. Do not configure a POP3 receive location to monitor a mailbox if you do not want the e-mail in the mailbox to be deleted.  
  
## See Also  
 [Configuring the POP3 Adapter](../core/configuring-the-pop3-adapter.md)
