---
title: "How to Configure Filters for a Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filters, configuring"
  - "filters, send ports"
  - "configuring, filters"
  - "managing [send ports], configuring"
  - "send ports, configuring"
  - "send ports, filters"
  - "managing [send ports], filters"
ms.assetid: ad13ca8e-bb1d-4449-8163-49dd9d5d92f8
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Filters for a Send Port
This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure filters for a send port. You can use filters to create simple messaging or content-based routing (CBR) applications. A filter sets conditions for message properties or fields that determine which messages are routed to the send port. A filter does not filter the messages that an orchestration routes to the send port.  
  
 You can create one or more filter expressions, which consist of a message property, an operator, and a value that is validated against the property by using the operator.  
  
 For example, you might create an expression like the following:  
  
 MSMQ.MsgID = 1  
  
 With this filter, the send port group would only subscribe to messages having an MSMQ message ID of 1.  
  
 You can create additional expressions and specify that they have an AND or OR relationship with other expressions, for example:  
  
 MSMQ.MsgID = 1 OR  
  
 SMTP.From = MyServer  
  
 In this case, the send port group would subscribe to all messages that have either an MSMQ message ID of 1 or that have been sent from the SMTP server named MyServer.  
  
> [!NOTE]
>  If you create a filter for a send port in one application that uses a property schema in another application, and then import the first application into a new BizTalk group, you will not receive a warning that the schema is missing, and filtering will not function when the application is installed and started. You can correct the problem by importing the application that contains the schema before you install the application that does not contain the schema.  
  
> [!NOTE]
>  The application developer can configure filters for a send port during the development process by using the procedure in this topic.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure filters for a send port  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure send port filters.  
  
3. Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Filters**.  
  
4. Configure filters as described in the following table, and then click **OK**.  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Delete**|Click to delete the selected filter expression.|  
   |**Move Up**|Click to move the selected property ahead in the filter expression sequence.|  
   |**Move Down**|Click to move the selected property down in the filter expression sequence.|  
   |**Property**|In the list, click a message property to use in this filter expression.|  
   |**Operator**|Type or select the operator for the expression.|  
   |**Value**|Type the value to validate against the property. The accepted value type varies according to the type of property. To see what type of value is accepted for a property, hover your mouse over the property. Acceptable values are as follows: Int: (Integer) This must be a whole number. String: A character string. dateTime: A date and/or time in .NET-supported format. For more information about .NET-supported time formats, see "DateTimeFormatInfo Class" in .NET Frameworks Help.|  
   |**Group by**|Select **And** or **Or** to indicate the relationship between this and other filter expressions.|  
  
## See Also  
 [Creating and Configuring Send Ports](../core/creating-and-configuring-send-ports.md)