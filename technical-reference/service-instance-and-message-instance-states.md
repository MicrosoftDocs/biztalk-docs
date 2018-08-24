---
title: Service Instance and Message Instance States
TOCTitle: Service Instance and Message Instance States
ms:assetid: 2666a27c-e5f7-4ae6-8f12-afa06bba8876
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559264(v=BTS.80)
ms:contentKeyID: 51526908
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.servicemessageinstance.properties
---

# Service Instance and Message Instance States

 

Service instance states and message instance states are displayed on the Group Hub page. They convey information about successfully processed messages and instances, failures, and suspensions during a specified time interval. Following is an explanation of each message instance and service instance state.

## Service Instance States

## UIElement List

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Service Instance state value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Ready to Run</strong></td>
<td>A service instance has received an activation message, but hasn't started yet. When the number of ready-to-run instances continually increases, the resources to process the workload may be insufficient or unavailable.</td>
</tr>
<tr class="even">
<td><strong>Scheduled</strong></td>
<td>Scheduled is a ready-to-run sub-state in which a service is ready to process but will commence processing only within a specified window of time (service window). The service window can be specified by the user in the properties dialog box for the port. Outside of that service window, the service is shown as &quot;scheduled.&quot;<br />
<br />
Note that when you suspend a scheduled instance and then resume it, the instance goes into a dehydrated state.</td>
</tr>
<tr class="odd">
<td><strong>Retrying</strong></td>
<td>A send port instance periodically re-tries to send a message, typically because the destination URI is unavailable. You can set the retry interval and count in the port properties dialog box.</td>
</tr>
<tr class="even">
<td><strong>Dehydrated</strong></td>
<td>The orchestration instance is idle and not in memory. Dehydrated is essentially the same state as Retrying, but it relates to an orchestration instead of to a message port. A Dehydrated orchestration typically is reactivated when it receives a message.</td>
</tr>
<tr class="odd">
<td><strong>Completed with discarded messages</strong></td>
<td>The service instance was completed, but some messages were not consumed by the instance.</td>
</tr>
<tr class="even">
<td><strong>Suspended, Resumable</strong></td>
<td>The service instance is suspended. You may be able to resume the service instance by means of an API call or an administrative action. <strong>Important:</strong> Resuming a messaging instance will do the following:
<ul>
<li>Resume the messaging instance.</li>
<li>Send the message to the send port.</li>
<li>The send port delivers the message to the destination; even if the send port is not in a Started state.</li>
</ul>
 <br />
<br />
Note that when you suspend a scheduled instance and then resume it, the instance goes into a dehydrated state.</td>
</tr>
<tr class="odd">
<td><strong>Suspended, Non-resumable</strong></td>
<td>The service instance is suspended, and cannot be resumed.<br />
<br />
Note that when you suspend a scheduled instance and then resume it, the instance goes into a dehydrated state.</td>
</tr>
<tr class="even">
<td><strong>Active</strong></td>
<td>The service instance is currently in memory.</td>
</tr>
<tr class="odd">
<td><strong>In Breakpoint</strong></td>
<td>The service instance has stopped execution at a pre-set breakpoint. You can make the service instance resume execution through the Orchestration Debugger or by right-clicking the service instance and selecting <strong>Resume</strong>.</td>
</tr>
</tbody>
</table>


## Message Instance States

## UIElement List

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Message state value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Delivered (not consumed)</strong></td>
<td>The message has been delivered to the engine, is being processed, and is in memory. It is considered delivered.</td>
</tr>
<tr class="even">
<td><strong>Consumed</strong></td>
<td>The message has been processed by a service instance. The service that processed holds onto the reference so that it can access the message later. The message is considered delivered. For example, MSMQ messages are in the Consumed state during batched resending of messages. MSMQ can be blocked while it waits for an acknowledgement, and the messages will be flagged as Consumed until the acknowledgement arrives, at which time MSMQ will restart to send messages.</td>
</tr>
<tr class="odd">
<td><strong>Suspended, Resumable</strong></td>
<td>The service instance associated with the message is suspended, and can be resumed. <strong>Important:</strong> Resuming a messaging instance will do the following:
<ul>
<li>Resume the messaging instance.</li>
<li>Send the message to the send port.</li>
<li>The send port delivers the message to the destination; even if the send port is not in a Started state.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Suspended, Non-resumable</strong></td>
<td>The service instance associated with the message is suspended, and cannot be resumed.</td>
</tr>
<tr class="odd">
<td><strong>Undelivered</strong></td>
<td>There may be no services available to process the message, or there may be no services running. For example, in an ordered delivery scenario, a message is Undelivered when another message that precedes it is being retried by the ordered delivery send port.</td>
</tr>
<tr class="even">
<td><strong>Undelivered (retrying)</strong></td>
<td>The message is associated with a send port that is attempting to resend it because the destination URI is unavailable (see &quot;Retrying&quot; service instance, in &quot;Service Instance States,&quot; above).</td>
</tr>
<tr class="odd">
<td><strong>Undelivered (scheduled)</strong></td>
<td>The message is waiting to be sent by a send port that has a service window set.</td>
</tr>
</tbody>
</table>


## See Also

[Viewing Tracked Message and Instance Data](https://msdn.microsoft.com/en-us/library/aa561587\(v=bts.80\))

