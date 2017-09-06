---
title: "Defining the Time Window and Time Slice Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [BAM], aggregations"
  - "managing [BAM], real-time data"
  - "Primary Import database [BAM], time properties"
  - "aggregations [BAM], managing"
  - "Primary Import database [BAM], real-time data"
  - "BAMConfiguration.xml file"
  - "aggregations [BAM], real-time data"
ms.assetid: 7f07b179-da10-4702-baf7-69516c8f16a6
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Defining the Time Window and Time Slice Properties
Administrators use the TimeWindow and the TimeSlice properties in the BAMConfiguration.xml file to define the life of the data in the real-time aggregation tables in the BAM primary import database.  
  
> [!NOTE]
>  To enact the changes they make in the BAM configuration file, administrators must undeploy the current BAM configuration, and then deploy the updated BAMConfiguration.xml.  
  
 For information about undeploying a BAM definition, see [How to Remove BAM Definitions](../core/how-to-remove-bam-definitions.md). For information about deploying a BAM definition, see [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).  
  
 If you want to change the TimeWindow and TimeSlice values without undeploying the BAM infrastructure, you can modifying the columns in the BAM_Metadata_Activities table in the BAM primary import database.  
  
## TimeSlice  
 You use the TimeSlice property to group completed BAM instance data. The TimeSlice property uses time that the data is written to the BAM primary import database to group BAM instance data.  
  
 For example, instance A is completed and persisted in the BAM primary import database at 1/1/2000 1:02 a.m. Instance B is completed and persisted in the BAM primary import database at 1/1/2000 1:04 a.m. If you set the value of the TimeSlice property to five minutes, instance A and instance B are grouped together.  
  
#### To change the TimeSlice value in the BAM Configuration file  
  
-   Change the value in this line of the BAM Configuration file:  
  
    ```  
    <Property Name="RTATimeSlice">5</Property>  
    ```  
  
#### To change the TimeSlice value in the BAM_Metadata_Activities table  
  
-   Modify the RTATimeSlice values, located in the bam_Metadata_Activities table in the BAMPrimaryImport database. If you deploy multiple real-time aggregations (RTA) for one or more activities, you have the option to specify a different time window for each RTA.  
  
    > [!NOTE]
    >  The value of RTAWindow must be an integer and the time unit is always minutes.  
  
## TimeWindow  
 When you run the CubeUpdate DTS package, the package moves data from the BAM primary import database into the BAM cubes. The package moves real-time aggregation data as grouped BAM data instances after all of the data in the group is older than the age specified in the RTA window property.  
  
#### To change the TimeWindow value in the BAM Configuration file  
  
-   Change the value in this line of the BAM Configuration file:  
  
    ```  
    <Property Name="RTAWindow">60</Property>  
    ```  
  
#### To change the TimeWindow value in the BAM_Metadata_Activities table  
  
-   Modify the RTAWindow values, located in the bam_Metadata_Activities table in the BAMPrimaryImport database. If you deploy multiple real-time aggregations (RTA) for one or more activities, you have the option to specify a different time window for each RTA.  
  
    > [!NOTE]
    >  The value of RTAWindow must be an integer and the time unit is always minutes.  
  
## See Also  
 [BAM Configuration Schema](../core/bam-configuration-schema.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)