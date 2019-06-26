---
title: Subscription Details Properties Dialog Box
TOCTitle: Subscription Details Properties Dialog Box
ms:assetid: 22ed4779-bb6c-473e-805c-18e82361bb98
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559194(v=BTS.80)
ms:contentKeyID: 51526798
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.subscriptiondetails
---

# Subscription Details Properties Dialog Box

 

The Subscription Details window enables you to examine subscriptions in the BizTalk Server engine.

## General Tab

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Type</strong></td>
<td>Displays whether the selected subscription is an instance subscription or an activation subscription. Activation subscriptions start new instances of a service, such as an orchestration or a send port. Instance subscriptions are created by service instances already running. These are created at runtime on the MessageBox on which the service instance exists and then copied to the master MessageBox.</td>
</tr>
<tr class="even">
<td><strong>Priority</strong></td>
<td>Displays the order in which messages are retrieved from the queue. When a message is routed by way of a given subscription, the message reference, which is put in the application's queue, is given the priority of the subscribing subscription. Messages with higher priority are dequeued first.</td>
</tr>
<tr class="odd">
<td><strong>State</strong></td>
<td>Displays the current state of the selected subscription. Subscription states displayed may be Started, Stopped, or Disabled.</td>
</tr>
<tr class="even">
<td><strong>Ordered Delivery</strong></td>
<td>Specifies whether Ordered Delivery was selected for a send port or orchestration receive port. When <strong>Ordered Delivery</strong> is True, messages must be processed through the port in a specified order. <strong>Ordered Delivery</strong> is important for messages that must be processed as a convoy. Ordered Delivery is false in all other circumstances.</td>
</tr>
<tr class="odd">
<td><strong>Request/Response</strong></td>
<td>Displays whether the receive port is a request-response port. When <strong>Request/Response</strong> is <strong>True</strong>, messages routed to this subscription generate a response message. This property is set by Solicit-Response send ports and by Request-Response orchestration receive ports.</td>
</tr>
<tr class="even">
<td><strong>Creation Time</strong></td>
<td>Displays the time when the subscription was created.</td>
</tr>
<tr class="odd">
<td><strong>Valid From</strong></td>
<td>Displays the absolute time, set by the messaging engine, before which the engine cannot read and process a message. This value is copied into the queue table from which the engine reads messages. Two common cases where this value is applied are retries on send ports and delay shapes in orchestrations. You do not set this property anywhere in BizTalk Server, and it will nearly always be zero.</td>
</tr>
<tr class="even">
<td><strong>Start Window</strong></td>
<td>Displays the time the port begins to transmit. This property applies to ports configured with a service window.</td>
</tr>
<tr class="odd">
<td><strong>End Window</strong></td>
<td>Displays the time the port ceases to transmit. This property applies to ports configured with a service window.</td>
</tr>
<tr class="even">
<td><strong>Subscription ID</strong></td>
<td>Displays the unique ID of the subscription.</td>
</tr>
<tr class="odd">
<td><strong>Service class</strong></td>
<td>Displays the kind of subscription selected.</td>
</tr>
<tr class="even">
<td><strong>Service name</strong></td>
<td>Displays the name of the service, such as an orchestration name or a port name.</td>
</tr>
</tbody>
</table>


## Expression Tab

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Property</strong></td>
<td>Displays the name of the context property used for subscription matching.</td>
</tr>
<tr class="even">
<td><strong>Operator</strong></td>
<td>Displays the mathematical operator used in the expression.</td>
</tr>
<tr class="odd">
<td><strong>Value</strong></td>
<td>Displays the value of the context property used for subscription matching.</td>
</tr>
<tr class="even">
<td><strong>Group by</strong></td>
<td>Displays a group of expressions that are connected through the AND operator during the subscription matching process. All expressions connected by AND must be true for a subscription to match the expression.</td>
</tr>
</tbody>
</table>


## See Also

[Service Instance and Message Instance States](service-instance-and-message-instance-states.md)

