---
title: "Send tracking data to Azure Application Insights using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3ff6cb9-44d0-46cd-9b4f-a346365afb7b
caps.latest.revision: 10
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Send tracking data to Azure Application Insights using BizTalk Server
Send [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] tracking data to Azure Application Inisights. 

**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can process and send your tracking data to Azure Application Insights. Use the Application Insights features to track your instances from receive ports, send ports, and orchestrations.

> [!IMPORTANT]
> This feature currently does not work with SQL Named Instances.

## Prerequisites
* Create a new instance of [Application Insights](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)
* Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

## Enable analytics for your environment

1. Open the **BizTalk Server Administration** console, expand **BizTalk Administration**, right-click the **BizTalk Group**, and select **Settings**. 
2. Check **Enable group-level analytics**.
3. For the **Target type**, select **Application Insight** from the list.
4. For the **Connection parameters**, enter your Application Insights **[instrumentation key](https://docs.microsoft.com/en-us/azure/application-insights/app-insights-create-new-resource)** (available in the Azure portal).

    Your Group settings look similar to the following: 

    ![Enable analytics for your environment](../core/media/environmentsettingapplicationinishgt.PNG)

5. Select **OK** to save your changes. 

Once enabled, [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] is ready to transmit data to Application Insights. Next, enable analytics on your ports and orchestrations. 

## Enable analytics on your artifacts

1. In BizTalk Server Administration, right-click a **receive port**, **send port** or **orchestration**, and select **Tracking**.
2. Under **Analytics**, check **Enable Analytics**. This setting starts tracking and transmitting data from the artifact to Application Insights.

    Your artifact settings look similar to the following: 
    
    ![Tracking data for Orchestration](../core/media/orchestrationsettingsapplicationinsight.PNG)

3. Select **OK** to save your changes.

Next, run queries within Application Insights to see your data.  

> [!TIP]
> Connect your BizTalk Server Analytics with other systems to gain even more insight into your organizations data.

## Run queries on your data
Once the data is sent to Application Insights, you can use the analytics tools within Azure to create advanced queries, and analyze your data.

1. Sign in to the [Azure Portal](https://portal.azure.com).
2. Open your Application Insights resource, and select **Analytics**.
3. Select **usage**, and run the query provided.

    > [!TIP]
    > Learn more about how to write queries in Application Insights at [Analytics in Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics).
    
## See also
 [Configure the Feature Pack](../core/configure-the-feature-pack.md)