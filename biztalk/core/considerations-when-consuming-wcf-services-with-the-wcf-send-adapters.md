---
description: "Learn more about: Considerations When Consuming WCF Services with the WCF Send Adapters"
title: "Considerations When Consuming WCF Services with the WCF Send Adapters"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Considerations When Consuming WCF Services with the WCF Send Adapters
This topic provides information that you should take into consideration when consuming WCF services with the WCF adapters.

## Use the "Template -- content specified by template" option when sending non-XML content as solicit messages
 The WCF adapters with **Body -- BizTalk response message body** (the default value) option do not allow sending non-XML message such as character data and bitmap images. You can use the **Template -- content specified by template** option for the WCF adapters to send non-XML messages. For more information about how to use the template, see [Considerations When Publishing WCF Services with the WCF Receive Adapters](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md).

## The WCF-BasicHttp and WCF-WSHttp send ports always ignore the proxy if the service address begins with http://localhost
 The WCF-BasicHttp and WCF-WSHttp send ports always ignore the proxy if the service address begins with http://localhost whether the proxy is configured on the **Proxy** tab of the send port or the **Proxy** tab of the send handler. You should use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same computer.

## The WCF-BasicHttp and WCF-WSHttp send adapters suspend the messages if the proxy setting is not correctly configured
 You can specify the proxy setting for the WCF-BasicHttp and WCF-WSHttp send adapters on the **Proxy** tab of the send port or the **Proxy** tab of the send handler. If this proxy setting is not correctly configured, the WCF adapters suspend the messages, and you receive the "There was no endpoint listening that could accept the message" error message in the event log.

## Setting up the permissions for a WCF send port with the WCF-NetMsmq adapter
 When a WCF send port with the WCF-NetMsmq adapter sends a message to a WCF service published with the NetMsmqBinding, it addresses the message to the target queue, which is the queue managed by the service's queue manager. The queue manager on the client sends the message to a transmission (or outgoing) queue. The transmission queue is a queue on the client-side queue manager that stores messages for transmission to the target queue.

 The service's queue manager accepts messages addressed to the target queues it owns and stores the messages. Then, the service makes requests to read from the target queue, and the queue manager delivers the messages to the service. For this reason, the service account for the BizTalk host instance hosting the send port should have the permissions to write on the transmission queue.

## Use an empty XPath expression to receive a SOAP message with character data in the content of the SOAP Body element
 The solicit-response WCF send port can receive a WCF message as a response message. To create a BizTalk message from an incoming response message with character data in the content of the SOAP **Body** element as shown in the following example, you should leave the **XPath expression** text box empty on the **Message** tab in the WCF adapter transport properties dialog box.

```
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">
    <s:Header>
      ...
    </s:Header>
    <s:Body>Contoso</s:Body>
</s:Envelope>
```

 If you select the **Envelope** or **Body** option, the adapter does not create the BizTalk message from the incoming message. The message is not suspended because messages that fail in the inbound SOAP marshaling processing are not suspended. For more information about how to use the XPath expression on the **Message** tab, see [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md).

> [!NOTE]
>  You can use the TraceViewer tool (SvcTraceViewer.exe) in the Windows SDK by configuring the BTSNTSvc.exe.config.file. For more information about the Windows SDK, see "What's New in the Windows SDK" at [https://go.microsoft.com/fwlink/?LinkId=75219](https://go.microsoft.com/fwlink/?LinkId=75219). For more information about the TraceViewer tool, see "TraceViewer Tool (SvcTraceViewer.exe)" at [https://go.microsoft.com/fwlink/?LinkId=75218](https://go.microsoft.com/fwlink/?LinkId=75218).

## BizTalk Server does not use multi-part message types and root elements describing custom SOAP headers
 If you run the BizTalk WCF service Consuming Wizard against metadata where custom SOAP headers are defined, the wizard generates root elements in the generated schemas to represent the custom SOAP headers. The wizard also creates multi-part message types in orchestrations for the custom SOAP headers. BizTalk Server. However, BizTalk Server does not use multi-part message types and root elements to handle the custom SOAP headers.

 To access custom SOAP headers, you should use the **InboundHeaders** property. For more information about receiving custom SOAP headers, see [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md). To use custom SOAP headers, you should use the **OutboundCustomHeaders** property. For more information about sending custom SOAP headers, see [SOAP Headers with Consumed WCF Services](../core/soap-headers-with-consumed-wcf-services.md).

## Create separate host instances for send ports that use different proxy addresses and/or proxy credentials
 To achieve the best possible performance for WCF send adapters, we recommend that you create separate host instances for send ports that use different proxy addresses and/or proxy credentials. This avoids contention on proxy settings.

## See Also
 [BTSNTSvc.exe.config File](../core/btsntsvc-exe-config-file.md)
