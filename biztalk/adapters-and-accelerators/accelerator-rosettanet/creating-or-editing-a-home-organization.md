---
title: "Creating or Editing a Home Organization | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "home organizations, about home organizations"
  - "home organizations, modifying"
  - "creating, home organizations"
  - "modifying, home organizations"
  - "home organizations"
  - "home organizations, creating"
ms.assetid: b54afb84-2f16-4516-8701-b03301476362
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating or Editing a Home Organization
This topic describes how to create or edit a home organization. The home organization configuration describes and classifies the organization, sets the non-repudiation of origin period, and provides contact information.  
  
 The home organization configuration does not include signing and decryption certificates, as the partner configuration does. You configure the signing certificate for the BizTalk Group in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration Console. You configure the decryption certificate for the BizTalk Hosts (BizTalkServerApplication and BizTalkIsolatedHost) in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
 You can create two home organizations within a single company or deployment. An example of this might be an instance in which you want to create priority handling of messages, in which messages bound for one organization would be a greater priority than messages bound for another. When you create multiple home organizations, you must provide each home organization with a separate DUNS number to identify them uniquely. The DUNS number is what defines the RosettaNet connection.  
  
 The settings in the home organization description are as shown in the following table, arranged by tab. For instructions on how to create and edit a home organization, see the procedures after the table.  
  
|Tab|Setting|Usage|  
|---------|-------------|-----------|  
|**General**|**Name**|The name for the home organization.<br /><br /> Required field.<br /><br /> Maximum length: 255|  
|**General**|**GBI**|The Global Business Identifier for the home organization. This must be nine digits in length, and must correspond to the DUNS number.<br /><br /> Required field.|  
|**General**|**Description**|A description that will help identify the home organization.|  
|**General**|**Home organization classification**|The nature of the organization.<br /><br /> Can be **End User**, **End User Government**, **Financier**, **Manufacturer**, **Retailer**, **Shopper**, **Freight Forwarder**, or **Marketplace**.<br /><br /> You can enter another value for the home organization classification in the service header of a message, overriding this property, by entering an HPCC custom property in the Custom Properties tab of the agreement. For more information, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).|  
|**Contact Properties**|**Contact name**|The name of the contact at the home organization.<br /><br /> Required field.|  
|**Contact Properties**|**E-mail address**|The e-mail address of the contact at the home organization.<br /><br /> Required field.|  
|**Contact Properties**|**Telephone number**|The telephone number for the contact at the home organization.<br /><br /> Required field.|  
|**Contact Properties**|**Fax number**|The fax number for the contact at the home organization.<br /><br /> Required field.|  
|**Contact Properties**|**Supply chain code**|The supply chain code for the home organization.<br /><br /> Required field.|  
  
### To create a home organization definition  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2. In the BTARN Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3. Right-click **Home Organizations**, point to **New**, and then click **Home Organization**.  
  
4. In the New Home Organization Properties dialog box, on the **General** and **Contact Properties** tabs, enter values for settings. For information about these settings, see the preceding table.  
  
5. Click **OK**.  
  
### To edit a home organization  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2. In the BTARN Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3. Click **Home Organizations**.  
  
4. Right-click the home organization you want to edit, and then click **Properties**.  
  
5. In the *\<home organization\>* Properties dialog box, on the **General** and **Contact Properties** tabs, change the settings as needed. For information about these settings, see the preceding table.  
  
6. Click **OK**.  
  
## See Also  
 [Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md)   
 [Administering the BTARN Configuration](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)