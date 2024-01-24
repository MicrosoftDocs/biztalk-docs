---
description: "Learn more about: Step 1: Create a Service Bus Namespace"
title: "Step 1: Create a Service Bus Namespace"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 1: Create a Service Bus Namespace
In this step, you create a [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)] namespace. You will use this namespace to host a relay endpoint for receiving opportunity notifications from Salesforce. Later in the process of creating this solution, you will use this relay endpoint to receive the notification message into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.  
  
### To create a [!INCLUDE[sb](../includes/sb-md.md)] namespace  
  
1.  Log on to [https://portal.azure.com](https://portal.azure.com) using your Microsoft account.  
  
2.  At the bottom of the page, click **New**, **App Services**, **Service Bus Relay**, and then **Quick Create**.  
  
3.  Enter the namespace as `BtsSalesforce` and select a region closest to your current geographical location. Click **Create a Relay**.  
  
    > [!CAUTION]
    >  This namespace must be globally unique. So, you must use a namespace other than one mentioned in this tutorial.  
  
    > [!NOTE]
    >  Note that the relay is not created as part of the operation, only the namespace is. The relay endpoint is created later in this tutorial when we configure a receive location for the **SB-Messaging** adapter.  
  
4.  After the namespace is created, the status is set to **Active**. Once the status is active, you can select the namespace and click **Access Key** at the bottom of the page to get details on how to connect to the **BtsSalesforce** namespace, including the values for **Default User** and **Default Key**. You will need these details later in the tutorial.  
  
## See Also  
 [Tutorial 6: Integrating BizTalk Server 2013 with Salesforce](tutorial-integrating-biztalk-server-2013-with-salesforce.md)
