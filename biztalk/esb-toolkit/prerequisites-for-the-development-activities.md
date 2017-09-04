---
title: "Prerequisites for the Development Activities | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54c91405-f9a4-4676-b5c5-fe90b3b51b45
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Prerequisites for the Development Activities
This section describes how to prepare your environment to complete the steps in the development activities that are included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. Complete the following setup before you attempt any of the procedures in the development activities:  
  
## Set up your computer to perform the procedures in the BizTalk ESB Toolkit development activities  
  
1.  Install and deploy the Itinerary sample application, the Dynamic Resolution sample application, and the Multiple Web Services sample application. For more information about installing and deploying these applications, see [BizTalk ESB Toolkit Sample Applications](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md).  
  
2.  Run the UDDI Publisher Utility.  
  
3.  On your development computer, in Windows Explorer, create the following paths:  
  
    -   C:\HowTos  
  
    -   C:\HowTos\Itineraries  
  
    -   C:\HowTos\DropFolder  
  
    -   C:\HowTos\Out  
  
4.  Ensure that your [!INCLUDE[prague](../includes/prague-md.md)] service account has **Full Control** permissions to the C:\HowTos directory structure.  
  
5.  Ensure that your Microsoft BizTalk Server service account has **Write** permissions to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out.  
  
6.  Copy the following test message to the C:\HowTos folder:  
  
    -   C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Test\Data\NAOrderDoc.xml  
  
7.  In the C:\HowTos folder, create a shortcut to the Itinerary Test Client application, found at the following location:  
  
    -   C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Source\ESB.Itinerary.Test\bin\Debug\ESB.Itinerary.Test.exe  
  
## Create the Visual Studio solution  
  
1.  In [!INCLUDE[vs2010](../includes/vs2010-md.md)], on the File menu, point to **New**, and then click **Project**.  
  
2.  In the **New Project** dialog box, in the Project types pane, click **Visual C#**, and then click **Class Library** in the Templates pane.  
  
3.  In the **Name** box, type **ItineraryLibrary**.  
  
4.  In the **Location** box, type **C:\HowTos**.  
  
5.  Select the **Create directory for solution** check box.  
  
6.  In the **Solution Name** box, type **Patterns**, and then click **OK** to create the solution.  
  
7.  Delete the **Class1.cs** file from the **ItineraryLibrary** project.