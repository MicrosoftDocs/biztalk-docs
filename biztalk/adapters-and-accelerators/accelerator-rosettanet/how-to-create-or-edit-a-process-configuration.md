---
title: "How to Create or Edit a Process Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "process configuration, modifying"
  - "process configuration, creating"
  - "authorization properties"
  - "non-repudiation, properties"
  - "creating, process configuration"
  - "modifying, process configuration"
ms.assetid: ef6160f1-f2f0-42ff-a516-7818c9d79d26
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create or Edit a Process Configuration
This topic describes how to create or edit a process configuration.  
  
 The settings in the process configuration are as shown in the following table, arranged by tab. Procedures for creating and editing a process configuration appear after the table.  
  
 The authorization and non-repudiation properties are interdependent. For more information about how to set these properties, see [Authorization and Non-Repudiation Properties](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md).  
  
|Tab|Setting|Usage|  
|---------|-------------|-----------|  
|**General**|**Display Code**|The Partner Interface Process (PIP) display code. This can correspond either to the RosettaNet PIP designation or to the name for a custom schema. It is recommended that you use a standard naming convention, such as a name including the process code and the version, for example, "STD_3A2_R02.00.00A". This will make it easier for you to maintain different versions of the same PIP.<br /><br /> Required field.|  
|**General**|**Process Code**|The three-digit PIP code. For example, "3A2".<br /><br /> Required field.|  
|**General**|**Version**|The version of the PIP. For example, "V02.02" or "R02.00.00A".<br /><br /> Required field.|  
|**General**|**Process Name**|The name of the PIP. For example, "Price and Availability Request Action".<br /><br /> Required field.|  
|**General**|**Description**|A description of the messages that conform to the PIP.|  
|**General**|**Standard**|The type of standard.<br /><br /> Possible values: RosettaNet (the default) or CIDX|  
|**General**<br /><br /> (Non-RosettaNet content area)|**Message standard**|For non-RosettaNet content, the name of the non-RosettaNet standard. Use this setting if you are not using a RosettaNet PIP, but have defined a custom schema. Use this setting for RNIF 2.0 only, not for RNIF 1.1 or CIDX.|  
|**General**<br /><br /> (Non-RosettaNet content area)|**Standard version**|For non-RosettaNet content, the version of the non-RosettaNet standard. Use this setting if you are not using a RosettaNet PIP, but have defined a custom schema. Use this setting for RNIF 2.0 only, not for RNIF 1.1 or CIDX.|  
|**General**<br /><br /> (Non-RosettaNet content area)|**Payload binding ID**|For non-RosettaNet content, the identification number of the payload content. Use this setting if you are not using a RosettaNet PIP, but have defined a custom schema. The party implementing the custom PIP should define this value. Use this setting for RNIF 2.0 only, not for RNIF 1.1 or CIDX.|  
|**Activity**<br /><br /> (Acknowledgement of Receipt area)|**Non-Repudiation Required**|Determines whether signal messages must be signed (with a message digest included in the acknowledgement message) and stored in their original form by the receiving party in the MessageStorageIn or MessageStorageOut table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive database, for non-repudiation purposes. The receiving party must store the signals for the period designated in the **Non-Repudiation of origin** property in the partner configuration.<br /><br /> Possible values: `True` (the default) or `False`<br /><br /> If `False`, signal messages will not be stored for non-repudiation purposes. Signal messages can be signed or not.<br /><br /> If `True`, inbound signal messages will be stored in their original form in the MessageStorageIn table. Outbound signal messages will be stored in their original form in the MessageStorageOut table. Signal messages must be signed.<br /><br /> For more information, see [Authorization and Non-Repudiation Properties](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md).|  
|**Activity**<br /><br /> (Acknowledgement of Receipt area)|**Time To Acknowledge (seconds)**|The time in seconds by which the initiator must receive the acknowledgement. If the initiator does not receive it by this time, the initiator will retry if the retries have not exceeded the **Retry** count (in the **Behavior** section of this tab).<br /><br /> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] measures the **Time To Acknowledge** value from the time the initiator sent out the action message successfully. The value is included in the delivery header. The value cannot be less than zero or greater than the **Time To Perform** value that is set on the same page.<br /><br /> You use this setting for signal messages (application acknowledgements) returned in RNIF 1.1 and 2.01 processing. You also use this setting for acceptance acknowledgements returned in RNIF 1.1 processing.<br /><br /> The default value is 7200 seconds (two hours).|  
|**Activity**<br /><br /> (Behavior area)|**Is Authorization Required**|Determines whether any incoming Action or Signal message must be signed. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will not accept a business document if the individual/role is not authorized to perform the activity.<br /><br /> Possible values: `True` (the default) or `False`<br /><br /> If `False`, outbound action and signal messages will not be signed. Inbound action and signal messages may be signed. If they are not signed, the system will authorize the partner using the delivery header.<br /><br /> If `True`, incoming messages must be signed. Outgoing messages may be signed. Outgoing messages are signed only if **Non-Repudiation of Origin and Content** is set to `True`.<br /><br /> For more information, see [Authorization and Non-Repudiation Properties](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md).|  
|**Activity**<br /><br /> (Behavior area)|**Is Persistent Confidentiality Required**|Determines whether encryption is required.<br /><br /> Possible values: **None** (the default) indicates that no encryption is required. **Payload** indicates that encryption of the service content and attachments is required. **Payload Container** indicates that encryption of the service content, attachments, and service header is required.<br /><br /> In RNIF 2.0, the preamble and delivery header are never encrypted. In RNIF 1.1, no message parts are encrypted. They are only signed.|  
|**Activity**<br /><br /> (Behavior area)|**Is Secure Transport Required**|Determines whether HTTPS transport is required.<br /><br /> Possible values: `True` (the default) or `False`|  
|**Activity**<br /><br /> (Behavior area)|**Is Single Action**|Determines whether messages are single-action or double-action.<br /><br /> Possible values: `True` (the default) or `False`<br /><br /> Single-action messages are Information Distribution or Notification. Double-action messages are Business Transaction, Request Confirm, Request/Response, or Query/Response.<br /><br /> If the standard is CIDX, **Is Single Action** must be **True**.|  
|**Activity**<br /><br /> (Behavior area)|**Is Synchronous**|Determines whether trading partners will exchange action messages synchronously or asynchronously.<br /><br /> Possible values: `True` or `False`(the default)<br /><br /> Not used for RNIF 1.1.|  
|**Activity**<br /><br /> (Behavior area)|**Non-Repudiation of Origin and Content**|Determines whether action messages must be signed and stored by the receiving party in their original received form in the MessageStorageIn or MessageStorageOut table of the BTARNArchive database, for non-repudiation purposes. The receiving party must store the action messages for the period designated in the **Non-Repudiation of origin** property in the partner configuration for non-repudiation purposes. If required, the action messages must be signed.<br /><br /> Possible values: `True` (the default) or `False`<br /><br /> If `False`, action messages will not be stored for non-repudiation purposes. Action messages can be signed or not.<br /><br /> If `True`, inbound action messages will be stored in their original form in the MessageStorageIn table. Outbound action messages will be stored in their original form in the MessageStorageOut table. Action messages must be signed.<br /><br /> For more information, see [Authorization and Non-Repudiation Properties](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md).|  
|**Activity**<br /><br /> (Behavior area)|**Retry Count**|The number of times that the process should retry the activity if transport or processing fails. If the retry count is 3, then the process will attempt the activity four times.<br /><br /> The default value is 3.<br /><br /> If communication is synchronous, then [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not use this field, because retries do not apply in synchronous transactions.|  
|**Activity**<br /><br /> (Behavior area)|**Time to Perform**|The period (in seconds) within which the process must complete the activity. The period begins when the initiator sends the first document. The initiator (not the responder) must make sure that the activity completes within this period. This value is in the delivery header.<br /><br /> The default value is 86400 seconds (24 hours).<br /><br /> The **Time To Perform** value must be greater than the **Time To Acknowledge** value that is set in the **Acknowledgement of Receipt** section of the same page.|  
|**Activity**<br /><br /> (General area)|**Type**|Determines the type of the activity.<br /><br /> Possible values: **Business Transaction**, **Information Distribution** (the default), **Notification**, **Query/Response**, **Request/Confirm**, or **Request/Response**|  
|**Initiator**<br /><br /> (Business Document area)|**Description**|A description of the initiator action's business document.|  
|**Initiator**<br /><br /> (Business Document area)|**Name**|The name of the initiator action's business document. For example, "Price and Availability Request".|  
|**Initiator**<br /><br /> (Business Document area)|**Version**|The version of the business document. For example, "V02_02_00" or "R02.00.00A".<br /><br /> You can find this version number at the beginning of the RosettaNet XML Message Guidelines .htm file that you download with the PIP specification .doc file and the PIP DTD from the RosettaNet organization.|  
|**Initiator**<br /><br /> (General area)|**Action**|A description of the initiator action. For example, "Synchronous Test Query Action".|  
|**Initiator**<br /><br /> (General area)|**Role**|The role of the initiator. For example, "Buyer" or "Payer".<br /><br /> The default value is "Initiator".|  
|**Initiator**<br /><br /> (General area)|**Role Description**|A description of the role of the initiator. For example, "The party issuing the payment".|  
|**Initiator**<br /><br /> (General area)|**Role Type**|The type of role of the initiator.<br /><br /> Possible values: **Organizational**, **Employee**, or **Functional** (the default)|  
|**Initiator**<br /><br /> (General area)|**Service**|The initiator service. For example, "Buyer Service" or "Payer Service".|  
|**Initiator**<br /><br /> (General area)|**Service Classification**|The type of initiator service. For example, "Business Service".|  
|**Responder**<br /><br /> (Business Document area)|**Description**|A description of the responder action's business document. For example, "Formally confirms the status of line items in a purchase order".|  
|**Responder**<br /><br /> (Business Document area)|**Name**|The name of the responder action's business document. For example, "Purchase Order Confirmation".|  
|**Responder**<br /><br /> (Business Document area)|**Version**|The version of the business document. For example, "V02.02.00" or "R02.00.00A". You can find this version number at the beginning of the RosettaNet XML Message Guidelines .htm file that you download with the PIP specification .doc file and the PIP DTD from the RosettaNet organization.|  
|**Responder**<br /><br /> (General area)|**Action**|A description of the responder action. For example, "Purchase Order Confirmation Action".|  
|**Responder**<br /><br /> (General area)|**Role**|The role of the responder. For example, "Seller".<br /><br /> The default value is "Responder".|  
|**Responder**<br /><br /> (General area)|**Role Description**|A description of the role of the responder. For example, "The party receiving payment".|  
|**Responder**<br /><br /> (General area)|**Role Type**|The type of role of the responder.<br /><br /> Possible values: **Organizational** (the default), **Employee**, or **Functional**|  
|**Responder**<br /><br /> (General area)|**Service**|The responder service. For example, "Seller Service".|  
|**Responder**<br /><br /> (General area)|**Service Classification**|The type of responder service. For example, "Business Service".|  
  
### To implement a new process configuration  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2.  In the BTARN Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Right-click **Process Configuration Settings**, point to **New**, and then click **Process Configuration**.  
  
4.  In the New Process Configuration Properties dialog box, on the **General**, **Activity**, **Initiator**, and **Responder** tabs, type values for the settings listed in the preceding table, and then click **OK**.  
  
### To edit a process configuration  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2.  In the BTARN Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Click **Process Configuration Settings**.  
  
4.  Right-click the process configuration that you want to edit, and then click **Properties**.  
  
5.  In the *\<process configuration\>* Properties dialog box, on the **General** and **Contact Properties** tabs, change the settings as required. For information about these settings, see the preceding table.  
  
6.  Click **OK**.  
  
## See Also  
 [Using the PIP Specification to Create a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)   
 [Authorization and Non-Repudiation Properties](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)   
 [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)   
 [Administering the BTARN Configuration](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)