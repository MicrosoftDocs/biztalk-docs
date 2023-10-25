---
title: Designing Metadata Artifacts for Host Files
description: Learn how to design metadata artifacts for host files and generate a Host Integration Server Definition XML (HIDX) file to use in Azure Logic Apps.
ms.prod: host-integration-server
ms.topic: how-to
ms.date: 10/25/2023

#CustomerIntent: As an integration developer, I need to design metadata artifacts for host files.
---

# Designing Metadata Artifacts for Host Files

This guide shows how to design metadata artifacts for host files. You can then save these metadata artifacts as Host Integration Server Definition XML (HIDX) files to use with the Host Files built-in, service provider-based connector in Azure Logic Apps.

## Prerequisites

- [Download and install Visual Studio](https://visualstudio.microsoft.com/downloads/). After installation, make sure that you also install the workload named **Desktop development with C++** in Visual Studio. Otherwise, you get the error **Exception from HRESULT 0x800A007C**.

- [Download and install the HIS Designer for Azure Logic Apps](https://aka.ms/his-desiner-logicapps-download). The only prerequisite is [Microsoft .NET Framework 4.8](https://aka.ms/net-framework-download).

- Enable Visual Studio support for the Flat File processor in Azure Logic Apps. For this task, follow these steps:

  1. Open Visual Studio. On the toolbar, open the **Tools** menu, and select **Options**.

  1. From the **Options** list, expand **Host Integration Server**, and select **Host Files**.

  1. On the **Host Environment** tab, select **Include support for Flat File Processor and Logic Apps**.

     :::image type="content" source="media/vsoptions-logicapps-his.png" alt-text="Include support for Flat File Processor and Logic Apps dialog":::

## Create a host file project

In Visual Studio, you can use the Host File project template to create metadata artifacts. You can then use these artifacts with the Host Files built-in, service provider-based connector in Standard workflows for Azure Logic Apps. To create a new host files project, follow these steps:

1. In Visual Studio, from the **File** menu, select **New** > **New Project**.

1. From the project template list, select **Host File** > **Next**.

1. In the **Configure your new project** box, change the details that you want, and select **Create**.

   :::image type="content" source="media/la-newproject-hisf1.png" alt-text="Screenshot shows Visual Studio and details for Configure your new project.":::

## Add a host file definition

To support the Host Files connector in Azure Logic Apps, you need to add a host file definition.

1. In Solution Explorer, open the new host file project's shortcut menu, and select **Add** > **Add Host File Definition**.

1. When the **Add New Item** box appears, in the **Name** property, provide a name for the host file definition, and select **Add**.

   These steps continue with the example name **HostFileDefinition1**.

1. After the Host File definition wizard launches, in the **Host Environment** box, select the **Host Environment** and the **Host Language**, based on the following table:

   | Host Environment | Host Language |
   |------------------|---------------|
   | **Host File for System z** (z series IBM mainframe systems) | COBOL |
   | **Host File for System i** (i Series IBM midrange systems) | COBOL or RPG |

1. When you're done, select **Create**.

After you finish with the wizard, the main design view appears for you to manually create or import metadata artifacts. For this task, continue to the next section.

## Design a metadata artifact

This section shows how to manually create a metadata artifact. To import a host definition instead, see [Importing Host Definitions](application-integration-importhostdefs.md).

The following table lists the components of the main design view:

| Component | Description |
|-----------|-------------|
| Tables folder | Groups data tables in the assembly. |
| Schemas folder | Groups variables with shared attributes. |
| Unions folder | Represents the equivalent of COBOL unions. |

### Add a table

1. In the main design view, open the **Tables** shortcut menu, and select **Add Table**.

   :::image type="content" source="media/la-newproject-add-hftable1.png" alt-text="Screenshot shows main design view, Tables shortcut menu, and selected option for Add Table.":::

1. Open the new table's shortcut menu, and select **Properties**. Provide values for each column's properties based on the following table:

   | Property | Description or value |
   |----------|----------------------|
   | **Alias** | A valid alias that starts with [A-Za-z], followed by alphanumeric characters with a maximum length of 256, for example, **CUSTOMER** |
   | **Host File Name** | A mainframe file name has up to 22 parts separated by a period (**.**). Each part is limited to 10 characters. The maximum total size is 44 characters, for example, **HISDEMO.NWIND.CUSTOMER** |
   | **Schema** | Represents the structure of the host file, including data types. |

   :::image type="content" source="media/la-newproject-hftableprop1.png" alt-text="Screenshot shows new table and properties.":::

### Add a schema

1. In the main design view, open the **Schemas** shortcut menu, and select **Add Schema**.

   :::image type="content" source="media/la-newproject-add-hfschema1.png" alt-text="Screenshot shows main design view, Schemas shortcut menu, and selected option for Add Schema.":::

   The designer creates a schema with one field.

1. To add another field, open the new schema's shortcut menu, and select **Add Field**. Repeat this step as necessary.

1. Open the new field's shortcut menu, and select **Properties**. Provide values for each field's properties based on the following table:

   | Property | Description or value |
   |----------|----------------------|
   | **Is Array** | If true, you must set the array dimensions, which support arrays with up to 7 dimensions and 16,777,215 elements. You must also enter values for the array properties **Occurs Count In** and **Occurs Depending On**. |
   | **Data Type** | The field's .NET data type |
   | **Name** | The field's name of the field |
   | **Error Handling** | Trigger an error, round, or truncate. |
   | **Host Data Type** | The field's COBOL or RPG data type |
   | **Size** | A 32-bit integer |
   | **String Delimiting** | **Null Terminated** or **Space Padded** |
   | **Trailing Filler** | For fields where the length is less than the specified maximum, you must specify the filler size. |

   :::image type="content" source="media/la-newproject-hfschemaprop1.png" alt-text="Screenshot shows new field and properties.":::

### Add a union

1. In the main design view, open the **Unions** shortcut menu, and select **Add Union**.

   :::image type="content" source="media/la-newproject-add-hfunion1.png" alt-text="Screenshot shows main design view, Unions shortcut menu, and selected option for Add Union.":::

   The designer creates a union with two members.

1. To add another member, open the new union's shortcut menu, and select **Add Union Member**. Repeat this step as necessary.

1. Open the member's shortcut menu, and select **Properties**. Provide values for each member's properties based on the following table:

   | Property | Description or value |
   |----------|----------------------|
   | **Is Array** | If true, you must set the array dimensions, which support arrays with up to 7 dimensions and 16,777,215 elements. You must also enter values for the array properties **Occurs Count In** and **Occurs Depending On**. |
   | **Data Type** | The member's .NET data type. This value can include structures defined in the previous section. |
   | **Name** | The member's name |
   | **Error Handling** | Trigger an error, round, or truncate. |
   | **Host Data Type** | The member's COBOL or RPG data type |
   | **Size** | A 32-bit integer |
   | **String Delimiting** | **Null Terminated** or **Space Padded** |
   | **Trailing Filler** | For members where the length is less than the specified maximum, you must specify the filler size. |

   :::image type="content" source="media/la-newproject-memberprop1.png" alt-text="Screenshot shows new union member and properties.":::

1. When you're done, continue to the next section to create the library that stores the metadata's design.

## Create the Host Integration Definition XML (HIDX) or metadata artifact

This section describes how to create the library that stores the metadata artifact's design.

1. To generate the metadata artifact, on the Visual Studio **File** menu or toolbar, select **Save All**. (Keyboard: Press Ctrl+Shift+S)

   :::image type="content" source="media/la-newproject-add-saveallhf.png" alt-text="Screenshot shows Visual Studio toolbar with selection option for Save All.":::

1. To find the generated HIDX file, go to your host file's folder.

   :::image type="content" source="media/la-newproject-outputhf-hidx.png" alt-text="Screenshot shows Visual Studio Output window with HIDX file location.":::

## Related content

- [Importing COBOL Host Definitions](application-integration-importhostdefs.md)
