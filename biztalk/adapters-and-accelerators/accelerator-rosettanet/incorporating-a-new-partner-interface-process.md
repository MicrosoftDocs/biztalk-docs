---
description: "Learn more about: Incorporating a New Partner Interface Process"
title: "Incorporating a New Partner Interface Process"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Incorporating a New Partner Interface Process
You can incorporate a new RosettaNet Partner Interface Process (PIP) schema in Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] assemblies by following these steps:

1. Download the PIP schema from the [GS1 US RosettaNet Standards website](https://www.gs1us.org/resources/rosettanet).

1. Deploy the schema to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] as part of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] RNPIPs assembly or as part of a separate [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] assembly. For more information, see [Extending BTARN with a New PIP](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md).

- Creating a new Process Configuration Setting in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console. For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).

  The downloaded schema is generally in .dtd format, with an accompanying PIP specification from the RosettaNet organization as a .doc file. The process of extending the pipeline to use the new schema includes converting the PIP .dtd file into an .xsd file.

  When you install [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes a number of XSD schemas. You can find those schemas in the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas folder. BTARN builds these schemas into an RNPIPs.dll file. If you have to change one of these schemas, you must open the RNPIPs project in the same folder, change the schema in BizTalk Editor, and then recompile and redeploy the assembly. After you redeploy the RNPIPs.dll file, you must redeploy the pipeline that uses the schema. You could use this process to incorporate a new schema in BTARN, but it is easier to extend the pipeline to include the new schema.

### To obtain the PIP schema

-   In your web browser, go to the [GS1 RosettaNet website](https://www.gs1us.org/resources/rosettanet).

## See Also
 [Extending BTARN with a New PIP](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md)
