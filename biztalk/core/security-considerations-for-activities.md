---
title: "Security Considerations for Activities | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fc49afd-a1c3-4ac7-8b89-11be667221e2
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Security Considerations for Activities
The security roles you use when intercepting the WCF adapter are the same as those used for other BAM solutions. The additional considerations for intercepting the WCF adapter involve selecting the correct user and event writer role to use.  
  
 When using WCF services and the WCF adapter, all BAM-related data is written to the BAM Primary Import database by the selected role.  
  
 You can select the proper user role configuration by assessing your solution scenario:  
  
- If your solution requires many new services that are tracked by many different activities, and are all run under the same user account, it is advantageous to use the BAM_EVENT_WRITER super role to write the intercepted events.  
  
  > [!NOTE]
  >  Users must be added to the BAM event writer super role. When adding a user to the super role it is important to remember that the user will then be able to write to all the activities in the system.  
  
- If your solution requires greater control of the events written, then you should use activity-specific roles.  
  
  > [!NOTE]
  >  Users must be added to the activity specific event writer role for each activity.  
  
  For more information about configuring the BAM event writer roles, see [How to Determine and Set Event Writer Roles for Activities](../core/how-to-determine-and-set-event-writer-roles-for-activities.md).  
  
> [!IMPORTANT]
>  You must be a member of the BizTalk Application Users group.  
  
 When selecting the user account to use when configuring the BAM WCF interceptor for impersonation security under IIS you should consider the following scenarios:  
  
- Self-Hosted: An executable running on your computer that holds the WCF service open.  
  
- WCF adapter: Solutions created using the **Biztalk WCF Service Publishing Wizard**.  
  
- IIS hosted: A solution hosted in an IIS application using a WCF Service.  
  
  Use the following table to help identify the account to use:  
  
|Solution type|Account to use|  
|-------------------|--------------------|  
|Self-hosted|The account that is used to run the executable that will hold the service open.|  
|WCF adapter|Use the AppPool identity: This is the AppPool associated with the Vroot that houses the receive location. This identity is created automatically when you use the **BizTalk WCF Service Publishing Wizard** to publish the site. You can consider this a special case of the IIS-hosted solution.|  
|IIS-hosted|The identity of the AppPool user running the WCF service VRoot/Application.|  
  
## See Also  
 [Security Considerations for BAM Interceptors](../core/security-considerations-for-bam-interceptors.md)