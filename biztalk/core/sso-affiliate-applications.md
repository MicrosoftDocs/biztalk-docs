---
title: "SSO Affiliate Applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSO, designing applications"
  - "applications [SSO], application types"
  - "SSO, application types"
  - "SSO, application properties"
  - "applications [SSO], properties"
  - "applications [SSO]"
  - "SSO, applications"
  - "applications [SSO], designing"
ms.assetid: 002ecf7e-4d52-425a-9498-0e7bd6545047
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO Affiliate Applications
The Enterprise Single Sign-On (SSO) Affiliate applications are logical entities that represent a system or sub-system such as a host, back-end system, or line of business application to which you are connecting using SSO. An affiliate application can represent a back-end system such as a mainframe or UNIX computer. It can also represent an application such as SAP, or a subdivision of the system, such as the "Benefits" or "Pay stub" sub-systems.  
  
 When the SSO administrator or the SSO Affiliate administrator defines an affiliate application, they must also determine who will administer the affiliate application (the application administrator), who the users of the affiliate application are (the application users), and what parameters the SSO system will use to authenticate the users of this affiliate application (the user ID, passwords, PIN numbers, and so on). For more information about application administrators and application users, see [SSO User Groups](../core/sso-user-groups.md).  
  
## Affiliate Application Types  
 Enterprise SSO defines several different application types. The different application types support different types of mappings between the Windows account and the account on the non-Windows system.  
  
 The application types are:  
  
 **Individual** Individual applications support one-to-one mappings between the Windows account and the non-Windows account. In an Individual type application, one Windows account is mapped to one, and only one, non-Windows account. The mapping can be used in either direction, from Windows to non-Windows, or from non-Windows to Windows, or both, depending on the flags that have been set for this application. Thus, Individual applications may be used for Windows initiated SSO, Host initiated SSO, or both.  
  
 **Group** Group applications support mappings between one Windows group to one single non-Windows account. The Application Users account is used to define the Windows group that will be used for this Group application. Only one mapping can be defined for a Group application, and that mapping must be between the Windows group and the single non-Windows account that will be used by all members of this Windows group to access the non-Windows system. Group applications may only be used for Windows initiated SSO.  
  
 **Host Group** Host Group applications are conceptually the reverse of Group applications. They support mappings between a defined group of non-Windows accounts to a single Windows account. The single Windows account that will be used by the non-Windows accounts is defined by the Application Users account for the application. The group of non-Windows accounts that is allowed to access this application is defined by creating a mapping for each non-Windows account. Host Group applications may only be used for Host initiated SSO.  
  
## Designing an Affiliate Application  
 Before creating an affiliate application, the SSO affiliate administrator or the SSO administrator has to make the following decisions:  
  
1. **What will this affiliate application represent?** You need to know the non-Windows application that the affiliate application will represent in the SSO system. For example,  
  
    Application name: APP1  
  
    Description: Application for Pay stub department  
  
    Contact: administrator@companyname.com  
  
2. **Who will administer this affiliate application?** You need to determine the administrators for this affiliate application. These form the Windows administrators group for this affiliate application. For example, Domain\APP1AdminGroup  
  
3. **Who will use this affiliate application?** You need to determine who the end-users are for this affiliate application. These users represent the Windows users group for this affiliate application; for example, Domain\DomainUsers. In the case of the application for Pay stubs, you might want all users to access their pay stub information, so you can specify the domain users group as the user group for this application.  
  
4. **What credentials does the affiliate application use to authenticate its users?** Different applications user different credentials to authenticate users. For example, some applications may use user IDs, passwords, PINs, or a combination of these. You must also determine whether the system needs to mask these credentials as the user provides them.  
  
5. **Will you use individual mappings or a group mapping for this affiliate application?** Does each Windows user have an account in the back-end system, or does the back-end system have one account for all Windows users? In the case of the pay stub system, each user has their own account to access their pay stub information, and you would need to use individual mappings.  
  
   After you create an affiliate application, you cannot modify the following properties:  
  
-   Name of the affiliate application  
  
-   Fields associated with the affiliate application  
  
-   Affiliate application type (host group, individual, or configuration store)  
  
-   Administration account same as affiliate administrators group. (If you select this property, then the affiliate administrators group is used as the application administrators account for this affiliate application.)  
  
## Affiliate Application Properties  
 The following table lists the properties you need to define for each affiliate application you create.  
  
|Property|Description|  
|--------------|-----------------|  
|Application name|Name of the affiliate application. You cannot change this property after you create the affiliate application|  
|Description|Brief description of the affiliate application|  
|Contact|The main contact for this affiliate application that users can use. (Can be an e-mail address.)|  
|appUserAccount|The Windows group that contains the user accounts of end-users that will be using this affiliate application|  
|appAdminAccount|The Windows group that contains the administrator accounts that will manage this affiliate application. **Note:**  You do not need to define this property if you set the adminAccountSame to Yes.|  
  
|Application Flag|Description|  
|----------------------|-----------------|  
|enableApp|The status of this affiliate application.|  
|groupApp|Determines whether this application uses a group mapping (yes) or individual mappings (No.)<br /><br /> You cannot change this property after you create the application.|  
|configStoreApp|Determines whether this affiliate application is a Configuration Store type application (yes).<br /><br /> You cannot change this property after you create the application.|  
|hostInitiatedSSO|Enable this if it is a host initiated SSO type application. Default is No.|  
|windowsInitiatedSSO|Enable this if it is a Windows initiated SSO type application. Default is Yes.|  
|validatePassword|This applies only to host initiated SSO applications. When the application attempts to retrieve credentials, it must provide the password in the SSO database which is used for validation by SSO services. Default is Yes.|  
|disableCredCache|The SSO Server stores credentials in a cache to expedite access. Default is No.|  
|allowTickets|Determines whether the SSO system uses tickets for this affiliate application.<br /><br /> **Security** You must be an SSO administrator to set this flag.|  
|validateTickets|Determines whether the SSO system validates tickets when the user redeems them.<br /><br /> **Security** You must be an SSO administrator to set this flag.|  
|appTicketTimeOut|Specifies a ticket timeout specific to the affiliate application. This can be set only when updating an affiliate application, not when creating it.<br /><br /> If ticketing is enabled for this application and this property is not, the timeout specified at the SSO System (Global) level is used.<br /><br /> **Security** You must be an SSO administrator to set this flag.|  
|timeoutTickets|Determines whether tickets have an expiration time. Default is Yes.<br /><br /> **Security** Unless it is required, do not disable ticket timeouts (No.).<br /><br /> **Security** You must be an SSO administrator to set this flag.|  
|allowLocalAccounts|Determines whether you allow the use of local groups and accounts in the SSO system. You can only configure this flag to Yes in single-computer scenarios.|  
|adminAccountSame|Determines whether to use the SSO affiliate administrator group as the application administrator group.<br /><br /> You cannot change this property after you create the application.<br /><br /> **Security** You must be an SSO administrator or SSO affiliate administrator to set this flag.|  
  
|Application Fields|Description|Description|  
|------------------------|-----------------|-----------------|  
|Field [0]|\<*credential*\>: Masked/Unmasked|Determines the type of credential (user ID, password, smartcard) that end users must provide to connect to the affiliate application, and whether this credential is masked (that is, whether the characters that the user types are displayed on the screen) or not.<br /><br /> You can enter as many fields as there are credentials for the affiliate application, but the first field must be the user ID.<br /><br /> You cannot change this property after you create the application.|  
  
## See Also  
 [Managing Affiliate Applications](../core/managing-affiliate-applications.md)   
 [SSO Mappings](../core/sso-mappings.md)   
 [Managing User Mappings](../core/managing-user-mappings.md)