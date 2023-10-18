---
title: "Designing Artifacts for Host Files | Microsoft Docs"
description: Designing Host Files for Azure Logic Apps
author: haroldcampos
ms.author: "hcampos"
ms.prod: "host-integration-server"
ms.topic: how-to
ms.date: "10/03/2023"
#CustomerIntent: As an integration developer I need to design mainframe metadata artifacts for Azure Logic Apps
---

# Designing Metadata Artifacts for Host Files

In this article, we will show you how to design Metadata Artifacts for Host Files. Metadata artifacts are saved as Host Integration Server Definition XML (HIDX) files.

## Prerequisites

You need to enable Visual Studio support for the Logic Apps Flat File Processor. To do this, conduct the following steps:

1. Open Visual Studio and in the menu, Select Tools. 
1. Select Options and select Host Integration Server. 
1. Check the  “Include support for Flat File Processor and Logic Apps” option in Host Files.

   :::image type="content" source="media/vsoptions-logicapps-his.png" alt-text="Include support for Flat File Processor and Logic Apps":::

## Host Files Projects

The Host Files project template is used to create metadata artifacts for the Host Files Logic Apps connector. It can also be used with the HIS Managed Provider for Host Files. The first step to Design a Metadata artifact is to create a new project. To do this, conduct the following steps:

1. Enter Visual Studio and select the Host Files project template
1. Select Create
   :::image type="content" source="media/la-newproject-hisf1.png" alt-text="Crea a Host File":::
1. Right Select on the HostFile node. As the Logic Apps connector for Host Files needs a Host File definition, the next step will be to Select on **Add Host File Definition**.
1. Once the **Add New Item dialog** appears, enter the name of the Host File Definition. Then the **Host Environment dialog** will appear. Here you will need to select a Host Environment and a Host Language. The Host Files Project support z Series (IBM Mainframes) and i Series (IBM Midranges) environments and COBOL and RPG languages respectively. Select Create.

## Designing Metadata Artifacts

Once the Host File Definition creation process has been completed, the main design view will appear. The purpose of the Design view is to either manually create or import the metadata artifact. The steps in this article cover the manual creation of a metadata artifact. For steps to Import a Host Definition please visit [Importing Host Definitions](application-integration-importhostdefs.md).

The following are the parts of the Main design view:

   |Use this  |To do this  |
   |---------|---------|
   |Tables directory     |     The  Tables directory is used to group the Data Tables in the assembly.     |
   |Schemas directory     |         The schemas directory allow the creation of group of variables with shared attributes|
   |Unions directory     |         These represent the equivalent of COBOL unions|

### Adding a Table

1. Right Select on the Tables directory and Select **Add Table**:
   :::image type="content" source="media/la-newproject-add-hftable1.png" alt-text="Visual Studio configuration for Logic Apps and HIS":::
1. Right Select on the created Table and Select Properties.
   :::image type="content" source="media/la-newproject-hftableprop1.png" alt-text="Table Properties":::
1. Configure the Table Properties using the following guidance:

   |Use this  |To do this  |
   |---------|---------|
   |Alias     |  A valid alias starts with [A-Za-z] followed by alphanumeric characters with maximum length of 256. For instance: "CUSTOMER"      |
   |Host File Name     | Mainframe file names are made of up to 22 parts separated by '.' and each part is limited to 10 characters. The maximum size is 44 characters.     For instance: "HISDEMO.NWIND.CUSTOMER".|
   |Schema     |    This represents the Schema with the structure of the Host File, including Data Types.     |

### Adding a Schema

1. Right Select on the Schemas directory and Select **Add Schema**:
   :::image type="content" source="media/la-newproject-add-hfschema1.png" alt-text="Adding schemas to a Host Definition":::
1. Right Select on the created Schema and Select new field. Repeat this procedure as many times needed:
   :::image type="content" source="media/la-newproject-hfschemaprop1.png" alt-text="Addint a field to a Schema":::
1. Configure the field using the following guidance:

   |Use this  |To do this  |
   |---------|---------|
   |Data Type     | .NET Data type          |
   |Error Handling     |    Trigger an Error, Round or truncate.     |
   |Host Data Type     |COBOL or RPG Data type for the Parameter         |
   |Is Array     |   If true, Array Dimensions will need to be provided. Supports arrays of up to 7 dimensions and 16777215 elements. Also, Occurs Count In and Depending On will need to be entered.    |
   |Name     |   Name of the field      |
   |Size     |      A 32 bits Integer.   |
   |String Delimiting     |      Null Terminated or Space Padded   |
   |Trailing filler     |    For members whose length is less than the maximum specified, you must specify Size of Filler.     |

### Adding a Union

1. Right Select on the Unions directory and Select **Add Union**:
   :::image type="content" source="media/la-newproject-add-hfunion1.png" alt-text="Adding Unions to a Host Definition":::
1. The Designer will create a Union with two members. You can add more members and customize the properties of each member using the following guidance:

   |Use this  |To do this  |
   |---------|---------|
   |Data Type     | .NET Data type          |
   |Error Handling     |    Trigger an Error, Round or truncate.     |
   |Host Data Type     |COBOL or RPG Data type for the Parameter         |
   |Is Array     |   If true, Array Dimensions will need to be provided. Supports arrays of up to 7 dimensions and 16777215 elements. Also, Occurs Count In and Depending On will need to be entered.    |
   |Name     |   Name of the Member      |
   |Size     |      A 32 bits Integer.   |
   |String Delimiting     |      Null Terminated or Space Padded   |
   |Trailing filler     |    For members whose length is less than the maximum specified, you must specify Size of Filler.     |

## Creating the Host Integration Definition XML (HIDX) or Metadata Artifact

The last step is to create the library that will store the Design of the Metadata. To generate it only Select the Save All option.

   :::image type="content" source="media/la-newproject-add-saveallhf.png" alt-text="Save All to generate HIDX file":::

Once the library is saved, the HIDX file will be generated

   :::image type="content" source="media/la-newproject-outputhf-hidx.png" alt-text="HIDX file location":::

## Related content

- [Importing COBOL Host Definitions](application-integration-importhostdefs.md)
