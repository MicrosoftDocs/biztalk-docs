---
description: "Learn more about: Schema Samples"
title: "Schema Samples"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Schema Samples
The Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK includes a series of XSD schemas for RNIF and Partner Interface Process (PIP) processing. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses these schemas to process messages. You can modify these schemas for your own purposes, or use these to troubleshoot failures.  
  
 The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK provides three sets of schemas. These schemas are XSD schemas associated with RosettaNet PIPs, RosettaNet next-generation schemas, and RNIF schemas.  
  
## XSD Schemas associated with RosettaNet PIPs  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses these schemas to validate the service content of message instances. You can modify these schemas to change message processing. You can also use the schemas to validate message instances when troubleshooting errors in processing service content.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] has compiled these schemas into the RNPIPs assembly. You can modify any one of these schemas by undeploying the RNPIPs assembly, changing the schema, and then redeploying RNPIPs. You must be careful that you do not change the schema. If you change the schema, your changes may not comply with the corresponding RosettaNet PIP. You can also add a schema to RNPIPs. For more information, see [Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md).  
  
 The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs these schemas in \<*drive*\>:\Program Files\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas.  
  
## RNIF Schemas  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses these schemas to validate RNIF message parts, such as the preamble, service header, and delivery header. These also include schemas for acknowledgments and exceptions.  
  
 The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs these schemas in \<*drive*\>:\Program Files\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\RNIFSchemas.  
  
## RosettaNet Next-Generation Schemas  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses these schemas to validate messages conforming to next-generation schemas for RosettaNet. These schemas support XSD natively, instead of DTDs. To use these schemas, add them to the RNPIPs assembly as described in [Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md).  
  
 The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs these schemas in the \<*drive*\>:\Program Files\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas\Domain, \Interchange, and \Universal folders.  
  
## See Also  
 [PIP Implementation](../../adapters-and-accelerators/accelerator-rosettanet/pip-implementation.md)   
 [Working with PIPs](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)   
 [Samples](../../adapters-and-accelerators/accelerator-rosettanet/samples3.md)
