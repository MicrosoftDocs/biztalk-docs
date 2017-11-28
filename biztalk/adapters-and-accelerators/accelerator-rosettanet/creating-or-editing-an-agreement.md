---
title: "Creating or Editing an Agreement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agreements, about agreements"
  - "agreements, modifying"
  - "agreements, creating"
  - "agreements"
  - "trading partners, agreements"
  - "creating, agreements"
  - "modifying, agreements"
  - "agreements, trading partners"
ms.assetid: 4bbe4b57-d6ec-4448-9c80-2aecd98e0dc7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating or Editing an Agreement
This topic describes how to create or edit a trading partner agreement. A trading partner agreement configures the relationship between two trading partners, including their identities; the Partner Interface Process (PIP); the action, signal, and sync URLs; and the associated protocols.  
  
 A trading partner agreement includes the settings for a process configuration, home organization, partner, and agreement. All these settings are required for an agreement. You can create a process configuration based on either a RosettaNet PIP or a custom schema, but you must create the configuration. You must also define both a home organization and a partner organization. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] does not support message exchange between unknown parties.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processes and validates a message based on all of these settings. For example, for a CIDX message, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] validates based on the RosettaNet Implementation Framework (RNIF) version (1.1 only), 0A1 agreement (No 0A1 only), and `Is Single Action` property (single-action only). A CIDX message will validate only if you set the RNIF version to "1.1", the 0A1 agreement to "No 0A1", and the `Is Single Action` property to `True`. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] also validates that any agreement properties are consistent with process configuration profile settings. For example, it will verify that you have set the `Standard` property of the profile to "CIDX", and that the 0A1 agreement property of the agreement is set to "No 0A1".  
  
 If you change an agreement while a process is active, you may encounter unpredictable results. The changes to the agreement properties will apply as soon as you click **Apply** or **OK** to accept them, but you cannot predict which stage of a process is running. After you change the agreement, any new activity in a current process or any new process will use the changed agreement properties. However, a process running when you change the agreement may have already used the previous agreement properties for a message that it is processing.  
  
 After creating an agreement, you must activate it to enable messages associated with the agreement to be sent or received. You can also deactivate an agreement to prevent any messages associated with the agreement from being sent or received. You must deactivate an agreement to edit it, and then reactivate it after editing.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves this information in the TPAConfig table in the BTARNCONFIG database.  
  
 The settings in the trading partner agreement are as shown in the following table, arranged by tab. The default settings are the most typically used values. Procedures for creating and editing these settings appear after the table.  
  
|Tab|Setting|Usage|  
|---------|-------------|-----------|  
|**General**|**Name**|A unique name for the agreement, such as Fabrikam_To_Contoso_3A2.<br /><br /> Required field.|  
|**General**|**Process configuration**|The identifier for the PIP.<br /><br /> This number identifies which process configuration is associated with this agreement.<br /><br /> The default value is the first in the list of the process configurations. The drop-down list includes all previously entered process configurations.<br /><br /> Required field.|  
|**General**|**My Organization**|The home organization, selected from a drop-down list.<br /><br /> Required field.|  
|**General**|**Partner organization**|The partner organization, selected from a drop-down list.<br /><br /> Required field.|  
|**General**|**Description**|A description of the trading partner agreement.|  
|**General**|**RNIF version**|The version of the RNIF that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will use for agreement communications.<br /><br /> Can be **V01.10.00** or **V02.00.01** (the default).<br /><br /> Must be **V01.10.00** for CIDX.|  
|**General**|**Home role**|The role of the home organization.<br /><br /> Can be initiator role or responder role.|  
|**General**|**0A1 agreement**|Whether [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will return a Notification of Failure message (0A1 PIP) when a failure occurs.<br /><br /> Can be **No 0A1** (the default) or **0A1**.<br /><br /> Must be **No 0A1** for CIDX.|  
|**General**|**Usage**|Indicates the type of scenario that the agreement will use.<br /><br /> Can be **Test** (the default) or **Production**.|  
|**General**<br /><br /> (**Application adapter** area)|**Assembly Name**|The file name of the ApplicationAdapter that you can select from the file system.<br /><br /> The default value is an empty string.|  
|**General**<br /><br /> (**Application adapter area**)|**Class name**|The name of the class that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will use from the ApplicationAdapter.<br /><br /> The default value is \<none\>.|  
|**General**<br /><br /> (**Validation adapter area**)|**Assembly Name**|The file name of the ValidationAdapter that you can select from the file system. The default value is an empty string.|  
|**General**<br /><br /> (**Validation adapter area**)|**Class name**|The name of the class that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will use from the ValidationAdapter.<br /><br /> The default value is \<none\>.|  
|**Ports**|**Action URL**|The URL to which the home organization will transmit an action message. For example, http://FabrikamServer/BTARNApp/RNIFReceive.aspx.<br /><br /> This is a required field if the following are all true:<br /><br /> - The **Is Synchronous** process-configuration setting is `False`.<br /><br /> - The **Is Single Action** process-configuration setting is `True`.<br /><br /> - The **Home role** agreement setting is **Initiator**.<br /><br /> This is also a required field if the following are true (in which case, the **Signal URL** field is also required):<br /><br /> - The **Is Synchronous** process-configuration setting is `False`.<br /><br /> - The **Is Single Action** process-configuration setting is `False`.<br /><br /> - You must enter a valid URI in this field, one that starts with either "http://domain" or "https://domain".|  
|**Ports**|**Signal URL**|The URL to which the home organization will transmit a signal message. For example, http://FabrikamServer/BTARNApp/RNIFReceive.aspx.<br /><br /> This is a required field if the following are true:<br /><br /> - The **Is Synchronous** process-configuration setting is `False`.<br /><br /> - The **Is Single Action** process-configuration setting is `True`.<br /><br /> - The **Home role** agreement setting is **Responder**.<br /><br /> This is also a required field if the following are true (in which case, the **Action URL** field is also required):<br /><br /> - The **Is Synchronous** process-configuration setting is `False`.<br /><br /> - The **Is Single Action** process-configuration setting is `False`.<br /><br /> You must enter a valid URI in this field, one that starts with either "http://domain" or "https://domain".|  
|**Ports**|**Sync URL**|The URL that the home organization will use to establish a connection through the HTTP adapter. For example, http://FabrikamServer/BTARNApp/RNIFReceive.aspx.<br /><br /> This is a required field if the following are true:<br /><br /> - The **Is Synchronous** process-configuration setting is `True`.<br /><br /> - The **Home role** agreement setting is **Initiator**.<br /><br /> You must enter a valid URI in this field, one that starts with either "http://domain" or "https://domain".|  
|**Protocol**|**Digest method**|The protocol used to calculate the digest of incoming messages for non-repudiation purposes.<br /><br /> **Starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] and newer versions**, SHA2 support is automatically included. Options include: **MD5**, **SHA-1**, **SHA-256** (default), **SHA-384**, and **SHA-512**.<br /><br />For previous [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] versions, options include **MD5** or **SHA-1** (default).<br /><br /> The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receive pipeline receives and decrypts a message even if the protocol used to encrypt the message and the **Encoding** setting on this tab of the agreement do not match. Therefore, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] receives messages encrypted in either RC2-40 or 3DES.<br /><br /> All outgoing signed messages have a digest of SHA-1.|  
|**Protocol**|**Encode all parts**|Whether the system will encode all parts of the multipart message together.<br /><br /> Can be `True` or `False` (the default).<br /><br /> When`True`, all parts of the multipart message will be encoded together using the method indicated by the `Encoding` property.<br /><br /> When `False`, the system will only encode attachments using the method indicated by the `Encoding` property. (Attachments are always encoded by the send pipeline using the method indicated by the `Encoding` property.) By default, when you set this property to `False`, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] encodes the other parts of the message (four parts in RNIF 2.01, three parts in RNIF 1.1) in quoted-printable format.|  
|**Protocol**|**Encoding**|The protocol used to encode all parts (if the **Encode all parts** box is `True`) or the attachment (if the **Encode all parts** box is `False`).<br /><br /> Can be **8 bit**, **base 64** (the default), or **quoted-printable**.|  
|**Protocol**|**Encryption algorithm**|The algorithm used to encrypt incoming and outgoing messages.<br /><br /> **Starting with [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] and newer versions**, AES support is automatically included. Options include **RC2-40**, **3DES**, **AES128** (default), **AES192**, and **AES256**. <br /><br />For previous [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] versions, options include **RC2-40** (default) or **3DES**.<br /><br /> The encryption algorithm only takes effect if you have set the `Is Persistent Confidentiality Required` property to either **Payload** or **Payload Container** in the corresponding process configuration.|  
|**Protocol**|**Encryption direction**|Whether the system will encrypt the incoming message or the outgoing message, or both.<br /><br /> Can be **Inbound**, **Outbound**, or **Inbound/Outbound** (the default).<br /><br /> The encryption direction setting only takes effect if you have set the `Is Persistent Confidentiality Required` property to either **Payload** or **Payload Container** in the corresponding process configuration.|  
|**Custom Properties**|**Name**|Name of the custom property.<br /><br /> You can set custom properties on a per-agreement basis. If you create a new custom private process, you can use these custom properties in processing different agreements.<br /><br /> You can use the `RuntimeConfig.GetTPACustomConfigValue` method in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK to retrieve custom properties from the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration.<br /><br /> The `Name` property must be unique and not empty.<br /><br /> You can enter the following custom values:<br /><br /> - **AAR**. This is the Acceptance Acknowledgment Required custom property. This applies to RNIF 1.1 only. Set this to **false** (which is not case-sensitive) to require only a receipt acknowledgment, not an acceptance acknowledgment. If **AAR** is set to anything other than **false**, then the responder public process must send an acceptance acknowledgment, and the initiator public process will expect an acceptance acknowledgment. If AAR is set to false, the public processes will complete after the receipt acknowledgment.<br /><br /> - **HPCC**. This is the Home Partner Classification Code. This applies to RNIF 1.1 only. This enables you to set the GlobalPartnerClassificationCode element for the home partner in the service header of an outgoing message to the entry in the Value column. This value overrides the Home organization classification property in the Home Organization configuration. Use this custom property when the home organization can have more than one classification.<br /><br /> - **PPCC**. This is the Partner Profile Classification Code. This applies to RNIF 1.1 only. This enables you to set the GlobalPartnerClassificationCode element for the partner in the service header of an outgoing message to the entry in the Value column. This value overrides the Partner classification property in the Partner configuration. Use this custom property when the partner can have more than one classification.|  
|**Custom Properties**|**Value**|Value of the custom property.|  
  
### To create a trading partner agreement  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2.  In the BTARN Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Right-click **Agreements**, point to **New**, and then click **Agreement**.  
  
4.  In the New Agreement Properties dialog box, on the **General**, **Ports**, **Protocol**, and **Custom Properties** tabs, enter the values for settings. For information about these settings, see the preceding table.  
  
5.  Click **OK**.  
  
    > [!NOTE]
    >  BTARN will not accept messages related to the agreement until you activate the agreement.  
  
6.  Right-click the name of the agreement in the right pane, and then click **Activate**.  
  
> [!NOTE]
>  If you have already activated an agreement, you can right-click the name of the agreement in the right pane, and then click **Deactivate** to prevent any messages associated with the agreement from being sent or received.  
  
### To edit a trading partner agreement  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2.  In the BTARN Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click the **Agreements** node.  
  
3.  Right-click the agreement that you want to edit, and then click **Properties**.  
  
4.  In the **\<***agreement name***\>** Properties dialog box, on the **General** and **Contact Properties** tabs, change settings as needed. For information about these settings, see the preceding table.  
  
5.  Click **OK**.  
  
## See Also  
 [Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md)   
 [Administering the BTARN Configuration](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)