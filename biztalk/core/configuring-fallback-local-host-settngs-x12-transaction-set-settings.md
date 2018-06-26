---
title: "Configuring Fallback Local Host Settngs (X12-Transaction Set Settings) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68511199-a7ed-45b3-807d-70378b2c6ebb
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Fallback Local Host Settngs (X12-Transaction Set Settings)
To process an incoming interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must determine the schema that it needs to use in processing and validating the interchange. This consists of determining the target namespace associated with the schema, and determining the schema to be used. In this page of the fallback agreement, you specify the fallback target namespace. How [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the schema is described in [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).  
  
> [!NOTE]
>  This topic applies also to HIPAA-related settings.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
### To configure local host settings for transaction sets  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.  
  
2. In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Transaction Set Settings** section, click **Local Host Settings**.  
  
3. Select **Convert implied decimal format Nn to base 10 numeric value** to convert an EDI number that is specified with the format Nn into a base-10 numeric value in the intermediate XML in BizTalk Server.  
  
   > [!NOTE]
   >  After this conversion, the intermediate XML may fail length validation. This occurs because the number in the base-10 numeric format includes a decimal, making its length one greater than the number in Nn format. You can resolve this issue by adding a value of **1** to the minimum/maximum length value.  
  
4. Select **Create empty XML tags for trailing separators** to have the interchange sender include empty XML tags for trailing separators.  
  
5. For **Target Namespace**, enter (or select from the drop-down list) the target namespace that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses to determine the schema to process the received message with.  
  
6. Click **Apply** to accept the changes, or click **OK** to enter and validate the changes, and then close the dialog box.  
  
## See Also  
 [Configuring X12 Fallback Agreement Properties for Transaction Set Settings](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)