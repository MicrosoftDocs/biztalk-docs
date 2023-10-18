---
title: "Designing Mainframe Artifacts for Host Applications"
description: Designing Mainframe Artifacts for CICS and IMS applications.
author: haroldcampos
ms.author: "hcampos"
ms.prod: "host-integration-server"
ms.topic: how-to
ms.date: "10/17/2023"

#CustomerIntent: As a programmer I need to design artifacts for host applications (CICS/IMS)
---

# Designing Metadata Artifacts for Host Applications (CICS/IMS)

In this article, we will show you how to design Metadata Artifacts for Host Applications (CICS/IMS). Metadata artifacts are saved as Host Integration Server Definition XML (HIDX) files.

## Prerequisites

You need to enable Visual Studio support for the Logic Apps Flat File Processor. To do this, conduct the following steps:

1. Open Visual Studio and in the menu, select **Tools**.
1. Select **Options** and select **Host Integration Server**.
1. Check the  **“Include support for Flat File Processor and Logic Apps”** option in **Host Files**.

   :::image type="content" source="media/vsoptions-logicapps-his.png" alt-text="Include support for Flat File Processor and Logic Apps dialog":::

## Host Application Projects

The Host Application project template is used to create metadata artifacts for the IMS and CICS Logic Apps connectors. The first step to Design a Metadata artifact is to create a new project. To do this, conduct the following steps:

1. Enter Visual Studio and select the Host Application project template
1. Select **Create**
   :::image type="content" source="media/la-newproject-his1.png" alt-text="Create Host Application project":::
1. Select on the **Host Application** node. As the Logic Apps connectors use the .NET Client Definitions, the next step will be to select on **Add .NET client Definition**.
1. Once the Add New Item dialog appears, enter the name of the Client Definition. Then the .NET Client Wizard will appear.
1. Use the Library wizard page to identify the .NET client library you are creating.
   :::image type="content" source="media/la-clientwizard-libhis1.png" alt-text="Library wizard dialog":::
1. The Remote Environment wizard page will appear to identify the remote environment (Mainframe or Midrange) and programming model to be used. Please use the following guidance for the Remote Environment creation.

   |Use this |To do this   |
   |---------|---------|
   |Vendor   | Microsoft   |
   |Protocol     |  Select the appropriate network protocol to access the Mainframe or Midrange. The following values are available: TCP, HTTP or LU 6.2. LU 6.2 is not supported in the Logic Apps connectors.       |
   |Target Environment     |  Select the target system: CICS, IMS, System i, System Z, System i Distributed Program Call.       |
   |Programming Model    |    Select a  [Programming Model](choosing-the-appropriate-programming-model1.md).      |
   |Host Language     |    Select the language in use: COBOL or RPG.     |
   |Allow 32K in/out    |        Select this checkbox to use the full 32K of the COMMAREA when using the Link model. |

1. Select Create

## Designing Metadata Artifacts

Once the Wizard has been completed, the main design view will appear. The purpose of the Design view is to either manually create or import the metadata artifact. The steps in this article cover the manual creation of a metadata artifact. For steps to Import a Host Definition please visit [Importing Host Definitions](application-integration-importhostdefs.md).

The following are the parts of the Main design view:

|Use this  |To do this  |
|---------|---------|
|Component node     |    This is the root of the Metadata artifact. It stores the information about the Client library and the remote environment.     |
|Interface node     |     The interface node is used to group all the methods in a component.    |
|Data Tables directory     |     The Data Tables node is used to group the Data Tables in the assembly.     |
|Structures directory     |         The structures directory allow the creation of group of variables with shared attributes.|
|Unions directory     |         These represent the equivalent of COBOL unions.|

### Adding a Method

Methods will be used to expose the Mainframe Program Business Logic to the Logic Apps workflows.

1. Select on **Interface** and select **Add Method**.

   :::image type="content" source="media/la-newproject-add-method1.png" alt-text="Adding a method to an Interface":::

1. Configure the method using the guidance in [Method Properties](method-properties1.md).  

### Adding a Parameter or a Return value

Parameters will be used to pass and receive data between the Mainframe Program and Logic Apps workflows.

1. Select on the **Method node** and select **Add Parameter**.
   :::image type="content" source="media/la-newproject-add-parameter1.png" alt-text="Adding a Parameter to a Method":::
1. Configure the Parameter using the following guidance:

   |Use this  |To do this  |
   |---------|---------|
   |Data Type     |.NET Data type         |
   |Error Handling     |     Trigger an Error, Round or truncate.    |
   |Host Data Type     |   COBOL or RPG Data type for the Parameter.      |
   |Is Array     |  If true, Array Dimensions will need to be provided. Supports arrays of up to 7 dimensions and 16777215 elements. Also, Occurs Count In and Depending On will need to be entered.       |
   |Name     |      Name of the Parameter.   |
   |Parameter Direction     |  Direction of the Method Parameter: In, In/Out or Out.       |
   |Precision     |       Parameter Data precision.  |
   |Trailing Filler     |  For parameters whose length is less than the maximum specified, you must specify Size of Filler.       |

1. Select on the **Method node** and select **Add Return value**.
   :::image type="content" source="media/la-newproject-add-retval1.png" alt-text="Adding a return value for a method":::
1. Configure the Return Value  using the following guidance:

   |Use this  |To do this  |
   |---------|---------|
   |Error Handling     |     Trigger an Error, Round or truncate.    |
   |Host Data Type     |   COBOL or RPG Data type for the Return Value.      |
   |Is Array     |  If true, Array Dimensions will need to be provided. Supports arrays of up to 7 dimensions and 16777215 elements. Also, Occurs Count In and Depending On will need to be entered.       |
   |Precision     |       Parameter Data precision.  |
   |Return Type     |      .NET Data type of the Return Value.   |
   |Return Value positioned after     |  TBC.       |
   |Trailing Filler     |  For parameters whose length is less than the maximum specified, you must specify Size of Filler.       |
   |Use TICS Work Area     |  TBC.       |

### Adding a Data Table

1. Select on the **Data Table** directory and select **Add Data table**:
   :::image type="content" source="media/la-newproject-add-datatable1.png" alt-text="Adding a DataTable for the library":::
1. Select on the created Data Table and select **new Column**. Repeat this procedure as many times needed:
   :::image type="content" source="media/la-newproject-add-column1.png" alt-text="Creating a column for a DataTable. Repeat this as needed.":::
1. Configure the column using the following guidance:

   |Use this  |To do this  |
   |---------|---------|
   |Data Type     | .NET Data type          |
   |Error Handling     |    Trigger an Error, Round or truncate.     |
   |Host Data Type     |COBOL or RPG Data type for the Parameter.         |
   |Name     |   Name of the Column.      |
   |Precision     |      Column Data precision.   |
   |Trailing filler     |    For columns whose length is less than the maximum specified, you must specify Size of Filler.     |

### Adding a Structure

1. Select on the **Structure** directory and select **Add Structure**:
   :::image type="content" source="media/la-newproject-add-structure1.png" alt-text="Adding a structure to the library":::
1. Select on the created Structure and select **new Member**. Repeat this procedure as many times needed:
   :::image type="content" source="media/la-newproject-add-stmember1.png" alt-text="Adding a member to the structure.":::
1. Configure the member using the following guidance:

   |Use this  |To do this  |
   |---------|---------|
   |Data Type     | .NET Data type          |
   |Error Handling     |    Trigger an Error, Round or truncate.     |
   |Host Data Type     |COBOL or RPG Data type for the Parameter.         |
   |Name     |   Name of the Column.      |
   |Precision     |      Member Data precision.   |
   |Trailing filler     |    For members whose length is less than the maximum specified, you must specify Size of Filler.     |

### Adding a Union

1. Select on the **Union** directory and select **Add Union**:
   :::image type="content" source="media/la-newproject-add-union1.png" alt-text="Adding a Union to the library":::
1. The Designer will create a Union with two members. You can add more members and customize the properties of each member using the following guidance:

   |Use this  |To do this  |
   |---------|---------|
   |Data Type     | .NET Data type. This can include structures defined in the previous section.          |
   |Error Handling     |    Trigger an Error, Round or truncate.     |
   |Host Data Type     |COBOL or RPG Data type for the Parameter.         |
   |Name     |   Name of the Column.      |
   |Precision     |      Member Data precision.   |
   |Trailing filler     |    For members whose length is less than the maximum specified, you must specify Size of Filler.     |

## Creating the Host Integration Definition XML (HIDX) or Metadata Artifact

1. The last step is to create the library that will store the Design of the Metadata. To generate it only select the **Save All** button.

   :::image type="content" source="media/la-newproject-add-saveall.png" alt-text="Save All to generate the HIDX metadata artifact":::

1. You will find the HIDX file will be generated in the application directory.

   :::image type="content" source="media/la-newproject-output-hidx.png" alt-text="Location of the HIDX file":::

## Related content

- [Importing Host Definitions](application-integration-importhostdefs.md)
