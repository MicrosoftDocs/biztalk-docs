---
title: "Considerations for receiving database change notifications using the Oracle E-Business Suite adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95bbb19e-8d31-4b27-8cfe-6760e4bb0808
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations for receiving database change notifications using the Oracle E-Business Suite adapter
This topic provides some considerations and best practices that you must keep in mind while using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive database notifications from an Oracle database.  
  
## Considerations While Using the Adapter to Receive Notifications  
 You must consider the following while using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive query notifications.  
  
- The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] simply passes on the notification, which it receives from the Oracle database, to the adapter clients. The adapter does not distinguish between the notifications for different operations, i.e., the adapter does not have any information whether a particular notification is for an Insert operation or an Update operation.  
  
- The notification message for an operation is not affected by the number of records affected by that operation. For example, irrespective of the number of records inserted in an Oracle database table, the adapter clients receive only one notification message.  
  
- We recommend that the adapter client application contain the logic to interpret the kind of notification received from the Oracle database. The adapter client applications can do so by extracting the information in the **\<Info\>** element of the received notification message. Here’s an example of a notification message received for an Insert operation.  
  
  ```  
  <?xml version="1.0" encoding="utf-8" ?>   
  <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/">  
    <Details>  
      <NotificationDetails>  
        <ResourceName>SCOTT.ACCOUNTACTIVITY</ResourceName>   
        <Info>1</Info>   
        <QueryId>0</QueryId>   
      </NotificationDetails>  
    </Details>  
    <Info>Insert</Info>   
    <ResourceNames>  
      <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">SCOTT.ACCOUNTACTIVITY</string>   
    </ResourceNames>  
    <Source>Data</Source>   
    <Type>Change</Type>   
  </Notification>  
  ```  
  
   Notice the value within the **\<Info\>** element. This value provides information on the operation for which the notification message was received. Your application should have the functionality to extract the value within the **\<Info\>** element and then based on the value, perform subsequent tasks. The topic [Process Notification Messages to Complete Specific Tasks in Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md) has instructions on how to extract the value within the **\<Info\>** element.  
  
- Ideally, after the client application receives a notification, it should update the record for which the notification is already received so that the subsequent notifications are not for the same record. For example, consider an **ACCOUNTACTIVITY** table that has a **Processed** column. For all new records inserted into the **ACCOUNTACTIVITY** table, the value in the **Processed** column is always ‘n’. For example, after an insert operation, the records in the **ACCOUNTACTIVITY** table will look like the following:  
  
  |Account Transaction ID|Processed|  
  |----------------------------|---------------|  
  |10001|n|  
  
   To get notifications for the newly inserted record, the adapter client will set the **NotificaitonStatement** binding property as:  
  
  ```  
  SELECT * FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
  ```  
  
   After, receiving the notification, the client application must set the value of the **Processed** column to ‘y’ so that the notification statement does not operate on the record that was already notified for. So, to achieve this, the client application must perform an Update operation on the **ACCOUNTACTIVITY** table. After the Update operation, the same record in the **ACCOUNTACTIVITY** table will look like the following:  
  
  |Account Transaction ID|Processed|  
  |----------------------------|---------------|  
  |10001|y|  
  
   Interestingly, the Update operation will again send a notification to the adapter client and the whole process will be repeated again. So, the client application must have the required logic to discard such unwanted notifications.  
  
- If the **NotifyOnListenerStart** binding property is true, the adapter will send a notification to the adapter client every time the receive location starts. For more information on how to use the binding property and interpret the notification message, see [Receive Oracle E-Business Suite Database Change Notifications After a Receive Location Breakdown](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md).  
  
## Typical Orchestration for Receiving Notifications  
 This section outlines the typical orchestration flow for receiving notifications using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
1. The first thing that the orchestration must do is to check the kind of notification received. The things to check for are:  
  
   - Whether the notification was received for the receive location restart.  
  
   - Whether the notification was received for an operation on a database table, such as Insert, Update, or Delete.  
  
     The orchestration must include an **Expression** shape, and within that an xpath query, to decide what kind of message is received.  
  
2. After the notification type is available, the orchestration must include a decision block to perform specific actions based on the type of notification received. To achieve this, the orchestration must include a **Decide** shape. The **Decide** shape consists of a **Rule** block and an **Else** block. Within the **Rule** block, you must specify the condition and then include orchestration shapes to perform certain operations if the condition is met. Within the **Else** block, you must include orchestration shapes to perform certain operations if the condition is *not* met.  
  
   The preceding recommendations are described in detail in [Process Notification Messages to Complete Specific Tasks in Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md).  
  
## See Also  
 [Receive Oracle E-Business Suite Database Change Notifications using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-biztalk-server.md)