---
title: "Creating or Editing a Partner | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, trading partners"
  - "trading partners"
  - "modifying, trading partners"
  - "trading partners, creating"
  - "trading partners, modifying"
  - "trading partners, about trading partners"
ms.assetid: 63809035-65a5-472d-b2e5-359c8e9d9d8c
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating or Editing a Partner
This topic describes how to create or edit a partner. The partner configuration describes and classifies the partner, sets the non-repudiation of origin period, configures certificates for the partner, and provides contact information.  
  
 When you first create a partner, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] creates two send ports to be used by that partner, one asynchronous and one synchronous. These send ports are named \<*partner name*\>.Async send port and \<*partner name*\>.Sync send port. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] automatically enlists and starts these send ports based upon the partner agreement. You can view these ports in the BizTalk Administration Console.  
  
 Partner settings are as shown in the following table, arranged by tab. For instructions about how to create and edit a partner, see the procedures after the table.  
  
|Tab|Setting|Usage|  
|---------|-------------|-----------|  
|**General**|**Name**|The name for the trading partner.<br /><br /> Required field.<br /><br /> Maximum length: 255|  
|**General**|**GBI**|The Global Business Identifier for the partner. This must be nine digits long, and must correspond to the DUNS number.<br /><br /> Required field.|  
|**General**|**Description**|A description that identifies the partner.|  
|**General**|**Hold until**|The date on which [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will submit a message to the MessagesFromLOB table. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will not deliver this message until the **Hold until** date. Partners must agree on this date, based on when the receiving partner will be ready to receive the message. This setting may be useful if a partner will not be available to process messages, for example, during a holiday.<br /><br /> The default value is the current date.|  
|**General**|**Partner classification**|The type of the partner organization.<br /><br /> Can be **Carrier** (the default), **Distributor**, **End User**, **End User Government**, **Financier**, **Manufacturer**, **Retailer**, or **Shopper**.<br /><br /> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] includes the value of this field in the Service header.<br /><br /> You can enter another value for the partner classification in the service header of a message, overriding this property, by entering a PPCC custom property in the Custom Properties tab of the agreement. For more information, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).|  
|**General**|**Non-Repudiation of Origin**|The number of days [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will hold the wire format of a message in the MessageStorageIn or MessageStorageOut database for non-repudiation (to prove legally that it has received it). [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will stamp this date on each incoming or outgoing message.<br /><br /> The default value is 2485 days.<br /><br /> However, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will not delete a message from the database upon expiration of this period. If you want to delete these messages, develop an SQL script to delete old messages based on this date/time stamp.|  
|**General**<br /><br /> (**Public key certificates** area)|**Signature**|The public key certificate that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will use to verify the partner's signature on an incoming message. This certificate must be stored in the Other People certificate store in the Certificate (Local Computer) node in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.<br /><br /> The default value is \<none\>.|  
|**General**<br /><br /> (**Public key certificates** area)|**Encryption**|The public-key encryption certificate that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will use to encrypt outgoing messages to a partner. This certificate must be stored in the Other People certificate store in the Certificate (Local Computer) node in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.<br /><br /> The default value is \<none\>.|  
|**Contact Properties**|**Contact name**|The name of the contact at the partner.<br /><br /> Required field.|  
|**Contact Properties**|**E-mail address**|The e-mail address of the contact at the partner.<br /><br /> Required field.|  
|**Contact Properties**|**Telephone number**|The telephone number for the contact at the partner.<br /><br /> Required field.|  
|**Contact Properties**|**Fax number**|The fax number for the contact at the partner.<br /><br /> Required field.|  
|**Contact Properties**|**Supply chain code**|The supply chain code for the partner. For example, "Information Technology" or "Electronic Components".<br /><br /> Required field.|  
  
### To create a partner  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**Management Console**.  
  
2.  In the BTARN Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Right-click **Partners**, point to **New**, and then click **Partner**.  
  
4.  In the **New Partner Properties** dialog box, on the **General** and **Contact Properties** tabs, type values for the settings. For information about these settings, see the preceding table.  
  
5.  Click **OK**.  
  
### To edit a partner  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2.  In the BTARN Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click **Partners**.  
  
3.  Right-click the partner that you want to edit, and then click **Properties**.  
  
4.  In the **\<***partner***\>** Properties dialog box, on the **General** and **Contact Properties** tabs, change settings as needed. For information about these settings, see the preceding table.  
  
5.  Click **OK**.  
  
## See Also  
 [Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md)   
 [Administering the BTARN Configuration](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)