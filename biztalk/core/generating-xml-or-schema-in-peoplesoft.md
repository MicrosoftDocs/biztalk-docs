---
title: "Generating XML or Schema in PeopleSoft | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "generating schemas"
  - "schemas, generating"
  - "generating XML"
  - "XML, generating"
ms.assetid: adfe2936-0dc2-42d2-b26a-718f8cc57eff
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generating XML or Schema in PeopleSoft
The following procedure describes how to use PeopleSoft Enterprise to create an XML file and trigger a PeopleSoft event. To do this, you change something in the PeopleSoft environment. The change activates an XML file, which is sent to the file folder that you set in your orchestration to be monitored. Later, in BizTalk Server, you import the XML and generate a schema.  
  
> [!NOTE]
>  When you associate the Location with the MSEXTERNAL node, any change made to Location Value generates an XML document—triggering an event. After enlisting and starting your orchestration, you can navigate through the PeopleSoft screens to the LOCATION screen. If you make a change to Location Value and save your change, a corresponding XML appears in your \out directory.  
  
### To generate XML or Schema in PeopleSoft  
  
1. In the PeopleSoft application, point to **Set up Financials**, point to **Supply Chain**, point to **Common Definitions**, point to **Location**, and then select **Location**.  
  
2. On the **Location** screen, enter the following information:  
  
   - **Set ID:** Enter **SHARE**.  
  
   - **Location Code:** Enter a code that starts with `WKLOC`.  
  
     ![](../core/media/psadapter-18-task-sharesearch.gif "PSAdapter_18_Task_ShareSearch")  
  
3. Click **Search**, and then click **Correct History** to put the screen in **Edit** mode.  
  
    ![](../core/media/psadapter-19-task-correcthistory.gif "PSAdapter_19_Task_CorrectHistory")  
  
4. Make a change to a field on the screen, and then click **Save**.  
  
5. Point to **PeopleTools**, point to **Integration Broker**, point to **Monitor**, and then select **Monitor Message**.  
  
    ![](../core/media/psadapter-20-task-monitormessage.gif "PSAdapter_20_Task_MonitorMessage")  
  
6. Make sure that **Channel Type** is **Message Instance**, and then click **Refresh**.  
  
7. In the **Done** column, click the number.  
  
8. Scroll to the bottom of the list and click the **Details** link on a **LOCATION_SYNC** message.  
  
    ![](../core/media/psadapter-21-task-detailslink.gif "PSAdapter_21_Task_DetailsLink")  
  
9. Click **View XML** on a **MSEXTERNAL** Node.  
  
     ![](../core/media/psadapter-22-task-viewxml.gif "PSAdapter_22_Task_ViewXML")  
  
     Copy and paste the contents of the XML into a file that can be accessed by your BizTalk Server project.  
  
     ![](../core/media/psadapter-23-task-xmlresult.gif "PSAdapter_23_Task_XMLResult")  
  
10. Remember the location of the file;  you reference it in BizTalk Server.  
  
## See Also  
 [Appendix B: Using the PeopleSoft Application](../core/appendix-b-using-the-peoplesoft-application.md)