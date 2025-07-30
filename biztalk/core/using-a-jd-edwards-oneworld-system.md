---
description: "Learn more about: Using a JD Edwards OneWorld System"
title: "Using a JD Edwards OneWorld System"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
ms.custom:
  - sfi-image-nochange
---
# Using a JD Edwards OneWorld System
The JD Edwards OneWorld system is accessible from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system by using the JD Edwards OneWorld adapter. This adapter is one of a group of eight line-of-business (LOB) adapters shipped by Microsoft for use with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 The JD Edwards OneWorld lab work is divided into two parts. This first lab (Lab 1) allows you to use the JD Edwards OneWorld system without needing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or any Microsoft products. You will use the JD Edwards OneWorld Client tool to connect to a JD Edwards OneWorld database and locate a specific record based upon address.  
  
 In the second lab (Lab 2), you will create a BizTalk project and orchestration. After you create the application, you will deploy it and use it to connect to a JD Edwards OneWorld system by using the JD Edwards OneWorld adapter. The goal is to access data through the BizTalk application by using the adapter.  
  
## Prerequisites  
 To perform the procedures for this lab, you need to install the JD Edwards OneWorld client software and its latest update. To use any of the client software tools you will need a JD Edwards OneWorld database, network connectivity to that database, and a user account on that system. You do not need [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to complete this lab.  
  
## Lab 1 - Using a JD Edwards OneWorld System  
 In this lab, you will use the JD Edwards OneWorld system without using any components of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. The goals are to test your connectivity to JD Edwards OneWorld and to ensure that the second lab will work correctly. You will use the JD Edwards OneWorld SQL Plus tool to create and manipulate a data table in a JD Edwards OneWorld database.  
  
## Procedures for Lab 1 - Using a JD Edwards OneWorld System  
  
#### To log on to JD Edwards OneWorld by using a browser  
  
-   Log on to the JD Edwards OneWorld system by clicking the JD Edwards OneWorld icon. Enter your **User ID**, **Password**, and **Environment**, and then click **OK**.  
  
     ![Image that shows the OneWorld Sign On dialog box.](../core/media/f04db2ef-d587-4357-b9e8-c96319886e97.gif "f04db2ef-d587-4357-b9e8-c96319886e97")  
  
#### To locate and view JD Edwards OneWorld data  
  
1.  A successful logon places you at the **JD Edwards OneWorld Explorer**.  
  
     ![Image that shows the JD Edwards OneWorld Explorer window.](../core/media/14e8c206-7e38-48f8-9108-e32a7ac9a740.gif "14e8c206-7e38-48f8-9108-e32a7ac9a740")  
  
2.  Expand **Master Directory**, then **Foundation Systems**, then **Address Book**, and then **Daily Processing**.  
  
     ![Image that highlights Daily Processing.](../core/media/1f742221-00e5-4697-95ff-64aa63ed567a.gif "1f742221-00e5-4697-95ff-64aa63ed567a")  
  
3.  In the right-hand window, double-click **Address Book Revisions**.  
  
     ![Image that shows the Address Book Revisions window.](../core/media/a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031.gif "a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031")  
  
4.  For **Alpha Name**, enter `Ga`, select the **Display Address** check box, and then click **Find** on the toolbar.  
  
     ![Image that shows where to search for an address.](../core/media/2f58413f-41a9-4ed9-ba5c-1d6d59eafb01.gif "2f58413f-41a9-4ed9-ba5c-1d6d59eafb01")  
  
     In the **Address Book Revisions - [Work With Addresses]** dialog box, two records are displayed as a result of the search.  
  
     ![Image that shows the Address Book Revisions dialog box, with two records displayed as a result of the search.](../core/media/9284df4e-ca9b-48ab-b2bf-a90d765d4a05.gif "9284df4e-ca9b-48ab-b2bf-a90d765d4a05")  
  
     An alternative method of locating data is to clear the **Alpha Name** field, click in the text box above the **Address Number** column, and enter `500`. Click **Find** on the toolbar to display the search results.  
  
     ![Image that shows an alternative method to locate the data.](../core/media/a88bd867-9a16-416a-a43e-cdfcc65fc670.gif "a88bd867-9a16-416a-a43e-cdfcc65fc670")  
  
     In Lab 2, there will be instructions for using the JD Edwards OneWorld adapter to retrieve the information for an **Address Number** of `500`.  
  
5.  On the **File** menu, click **Exit** to exit the JE Edwards OneWorld Client session.  
  
## Summary  
 In this lab, you used the JD Edwards OneWorld Client tool to log on to the JD Edwards OneWorld system. After you were connected, you searched for specific data and viewed the data records returned.
