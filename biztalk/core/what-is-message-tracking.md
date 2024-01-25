---
description: "Learn more about: What is Message Tracking?"
title: "What is Message Tracking?"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# What is Message Tracking?
A message is an electronic instance of data, as typically exchanged between two running business processes or applications. A message instance is made up of a message body, message properties, and metadata.  
  
 You can use the BizTalk Server Administration Console to enable message body and message property tracking. There you can also view the tracked message body, including schema information, strong name, and all the promoted properties for the generated message.  
  
## Message Body  
 Tracking the message body provides a record of messages sent and received. You must have message body tracking turned on in order to save messages after service instances processing is complete. After you have set the tracking options, it can take a few minutes before you can view the messages.  
  
> [!IMPORTANT]
>  The SQL Server Agent service must be running on all MessageBox databases. The TrackedMessages_Copy_\<MessageBoxName\> job makes message bodies available to tracking queries and WMI. To efficiently copy the message bodies, they remain in the MessageBox database and are periodically copied to the BizTalk Tracking (BizTalkDTADb) database by the TrackedMessages_Copy_\<MessageBoxName\> job. Having the SQL Server Agent service running is also a prerequisite for the archiving and purging process to work correctly.  
  
 You can use tracked messages to provide confirmation of receipt, to enable troubleshooting, and to allow data mining of historical transactions. You can track the message bodies at the input and output of ports, pipelines, and orchestrations. You can recover these messages using the BizTalk Server Administration Console, using the Operations object model (OM) (recommended) or through Windows Management Instrumentation (WMI) application programming interfaces (APIs).  
  
 BizTalk Server does not track messages that do not successfully make it through one of the tracking points. In some cases—such as when a message is suspended because it is invalid, or if no host is expecting the message—it may be placed in the Suspended queue without being tracked. If you terminate this message there will be no record of it.  
  
> [!IMPORTANT]
>  Message body tracking is not a substitute for legally binding auditing, and does not support nonrepudiation.  
  
## Message Properties  
 Message properties include promoted properties, routing information, and trading partner data. Message property tracking enables you to locate a specific message from the thousands that you may have tracked, by providing a record of promoted properties for each message in the results list. You can then track a subset of the message itself, using one of these properties.  
  
 To track context properties, you define a property schema for the namespace used in the context to store the properties. From there, you can select the context properties you want to track. BizTalk Server tracks them in the same way it tracks promoted message properties.  
  
> [!NOTE]
>  Make sure you give different names to the properties in the schema. An error message appears if you create duplicate names.  
  
 For example, you could use the Schema Editor to promote the PO Number field from a Purchase Order schema. Then, using the Find Message View, you could find the message instances that contain a particular value for that tracked field, such as PO Number = 16995.  
  
 Message property tracking creates much less overhead than message body tracking, because message property tracking only tracks the selected fields. After you set the tracking options for the message property, it can take a few minutes before you can view the properties.  
  
## Metadata  
 Metadata, such as the message instance identifier, the orchestration or pipeline logging the message, the point at which the orchestration or pipeline logs the message, and other relevant tracking details. For a message in the MessageBox database to route to a business process, it must contain context properties such as message type and origin. These properties become metadata. Message and service instance tracking uses subscription criteria to query against this metadata.  
  
 Through the BizTalk Server Administration Console, you can promote context properties by selecting the particular system schema. The system schemas are located in the Applications\BizTalk.System\Schemas node. BizTalk Server tracks these context properties globally—that is, all messages now track the particular context property. This may significantly increase the size of the BizTalk Tracking database.  
  
## Sensitive Data  
 You can secure the following data ensuring that it does not appear in corresponding schemas property window and therefore becomes unavailable for tracking.  
  
-   Apply the **isSensitive** attribute to any sensitive properties in a property schema, so that it is no longer visible in the Message Property tracking configuration selections.  
  
-   All out-of-box transports contain passwords marked as sensitive, so the transports cannot be tracked.  
  
-   In addition, these sensitive properties are no longer in the Management database, so if you are setting tracking options directly in the database, they are unavailable for tracking.  
  
-   If you track outbound on-the-wire message bodies, message tracking removes all the transport properties from the shortcut of the tracked message body. Therefore, in addition to removing outbound transport properties from the shortcut of the tracked message body, message tracking also removes properties from inbound transports.  
  
    > [!IMPORTANT]
    >  A promoted property can contain sensitive data. If tracking queries from the Group Hub page track a property which includes sensitive data, any user with permissions to run the tracking queries can view this data.  
  
## See Also  
 [Manage and track BizTalk Server artifacts](managing-artifacts.md)
