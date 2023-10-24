---
title: Designing Mainframe Artifacts for Host Applications
description: Learn how to design mainframe artifacts for CICS and IMS applications.
ms.prod: host-integration-server
ms.topic: how-to
ms.date: 10/25/2023

#CustomerIntent: As a programmer, I need to design artifacts for CICS and IMS host applications.
---

# Designing Metadata Artifacts for CICS or IMS Host Applications

This guide shows how to design metadata artifacts for CICS or IMS host applications. You can then save these metadata artifacts as Host Integration Server Definition XML (HIDX) files.

## Prerequisites

- [Download and install Visual Studio](https://visualstudio.microsoft.com/downloads/). After installation, make sure that you also install the workload named **Desktop development with C++** in Visual Studio. Otherwise, you get the error **Exception from HRESULT 0x800A007C**.

- [Download and install the HIS Designer for Azure Logic Apps](https://aka.ms/his-desiner-logicapps-download). The only prerequisite is [Microsoft .NET Framework 4.8](https://aka.ms/net-framework-download).

- Enable Visual Studio support for the Flat File processor in Azure Logic Apps. For this task, follow these steps:

  1. Open Visual Studio. On the toolbar, open the **Tools** menu, and select **Options**.

  1. From the **Options** list, expand **Host Integration Server**, and select **Host Files**.

  1. On the **Host Files** tab, select **Include support for Flat File Processor and Logic Apps**.

     :::image type="content" source="media/vsoptions-logicapps-his.png" alt-text="Include support for Flat File Processor and Logic Apps dialog":::

## Create a host application project

In Visual Studio, you can use the Host Application project template to create metadata artifacts for the **CICS Program Call** and **IMS Program Call** connectors in Azure Logic Apps. To create a new host application project, follow these steps:

1. In Visual Studio, from the **File** menu, select **New** > **New Project**.

1. From the project template list, select **Host Application** > **Next**.

1. In the **Configure your new project** box, change the details that you want, and select **Create**.

   :::image type="content" source="media/la-newproject-his1.png" alt-text="Screenshot shows Visual Studio and details for Configure your new project.":::

## Add .NET client definitions

To support the Azure Logic Apps connectors that can access mainframe systems, you need to add .NET client definitions. 

1. In Solution Explorer, open the your new host application's shortcut menu, and select **Add** > **Add .NET Client Definition**.

1. When the **Add New Item** box appears, in the **Name** property, provide a name for the .NET client definition, and select **Add**.

   These steps continue with the example name **NetClnt1**.

1. After the .NET Client Definition wizard launches, in the **Library** box, provide a name for the interface to use for identifying the .NET client library that you want to create.

   This example continues with the interface name **IInterface1**:

   :::image type="content" source="media/la-clientwizard-libhis1.png" alt-text="Screenshot shows .NET Client Definition wizard and Library box.":::

1. When you're done, select **Next**.

1. In the **Remote Environment** box, identify the remote mainframe or midrange environment and the programming model to use by providing the following information:

   | Parameter | Value or action |
   |-----------|-----------------|
   | **Vendor** | **Microsoft** |
   | **Protocol** | Select the appropriate network protocol to access the mainframe or midrange system: <br><br>- **TCP** <br>- **HTTP** <br>- **LU 6.2** (Unsupported for Azure Logic Apps connectors) |
   | **Target Environment** | Select the target system: <br><br>- **CICS** <br>- **IMS** <br>- **System i** <br>- **System Z** <br>- **System i Distributed Program Call** |
   | **Programming Model** | Select a [programming model](choosing-the-appropriate-programming-model1.md). |
   | **Host Language** | Select the language in use: **COBOL** or **RPG** |
   | **Allow 32K in/out** | Select this option to use the full 32K of the [COMMAREA data area](https://www.ibm.com/docs/en/cics-ts/5.4?topic=programs-commarea) when you use the [LINK model](choosing-the-appropriate-programming-model1.md). |

1. When you're done, select **Create**.

After you finish with the wizard, the main design view appears for you to manually create or import metadata artifacts. For this task, continue to the next section.

## Design metadata artifacts

This section shows how to manually create a metadata artifact. To import a host definition instead, see [Importing Host Definitions](application-integration-importhostdefs.md).

The following table lists the components of the main design view:

| Component | Description |
|-----------|-------------|
| Component node | The root of the metadata artifact. Stores information about the client library and the remote environment. |
| Interface node |  Groups all the methods in a component. |
| Data Tables folder | Groups data tables in the assembly. |
| Structures folder | Groups variables with shared attributes. |
| Unions folder | Represents the equivalent of COBOL unions. |

### Add a method

For your metadata artifact, you can add a method to expose the mainframe program business logic to workflows in Azure Logic Apps.

1. In the main design view, open the new interface's shortcut menu, and select **Add Method**.

   :::image type="content" source="media/la-newproject-add-method1.png" alt-text="Screenshot showing main design view, Interface shortcut menu, and selected option for Add Method.":::

1. Open the method's shortcut menu, and select **Properties**. Provide values for the method's properties based on the article [Method Properties](method-properties1.md).

### Add a parameter or return value

After you add a method, you can define parameters and a return value to pass and receive data between the mainframe program and workflows in Azure Logic Apps.

1. In the main design view, open the new method's shortcut menu, and select **Add Parameter**.

   :::image type="content" source="media/la-newproject-add-parameter1.png" alt-text="Screenshot showing main design view, method shortcut menu, and selected option for Add Parameter.":::

1. Open the parameter's shortcut menu, and select **Properties**. Provide values for the parameter's properties based on the following table:

   | Property | Description or value |
   |----------|----------------------|
   | **Is Array** | If true, you must set the array dimensions, which support arrays with up to 7 dimensions and 16,777,215 elements. You must also enter values for the array properties **Occurs Count In** and **Occurs Depending On**. |
   | **Data Type** | The .NET data type for the parameter |
   | **Name** | The parameter's name |
   | **Parameter Direction** | Direction of the method parameter: **In**, **In/Out**, or **Out** |
   | **Error Handling** | Trigger an error, round, or truncate. |
   | **Host Data Type** | The COBOL or RPG data type for the parameter |
   | **Precision** | The parameter's data precision |
   | **Trailing Filler** | For parameters where the length is less than the specified maximum, you must specify the filler size. |

1. Open the new method's shortcut menu, and select **Add Return Value**.

   :::image type="content" source="media/la-newproject-add-retval1.png" alt-text="Screenshot showing main design view, method shortcut menu, and selected option for Add Return Value.":::

1. Open the return value's shortcut menu, and select **Properties**. Provide values for the return value's properties based on the following table:

   | Property | Description or value |
   |----------|----------------------|
   | **Is Array** | If true, you must set the array dimensions, which support arrays with up to 7 dimensions and 16,777,215 elements. You must also enter values for the array properties **Occurs Count In** and **Occurs Depending On**. |
   | **Return Type** | The .NET data type for the return value |
   | **Return Value Positioned After** | TBC |
   | **Use TICS Work Area** | TBC |
   | **Error Handling** | Trigger an error, round, or truncate. |
   | **Host Data Type** | The COBOL or RPG data type for the return value |
   | **Precision** | The parameter's data precision |
   | **Trailing Filler** | For parameters where the length is less than the specified maximum, you must specify the filler size. |

### Add a data table

1. In the main design view, open the **DataTables** shortcut menu, and select **Add DataTable**.

   :::image type="content" source="media/la-newproject-add-datatable1.png" alt-text="Screenshot showing main design view, DataTables shortcut menu, and selected option for Add Data Table.":::

1. Open the new data table's shortcut menu, and select **Add DataTable Column**. Repeat this step as necessary.

   :::image type="content" source="media/la-newproject-add-column1.png" alt-text="Screenshot showing a created column for a data table.":::

1. Open the column's shortcut menu, and select **Properties**. Provide values for each column's properties based on the following table:

   | Property | Description or value |
   |----------|----------------------|
   | **Data Type** | The .NET data type for the column |
   | **Name** | The column's name |
   | **Error Handling** | Trigger an error, round, or truncate. |
   | **Host Data Type** | The column's COBOL or RPG data type |
   | **Precision** | The column's data precision |
   | **Trailing filler** | For columns where the length is less than the specified maximum, you must specify the filler size. |

### Add a structure

1. In the main design view, open the **Structures** shortcut menu, and select **Add Struct**.

   :::image type="content" source="media/la-newproject-add-structure1.png" alt-text="Screenshot showing main design view, Structures shortcut menu, and selected option for Add Struct.":::

   The designer creates a structure with one member. 

1. To add another member, open the new structure's shortcut menu, and select **Add Structure Member**. Repeat this step as necessary.

   :::image type="content" source="media/la-newproject-add-stmember1.png" alt-text="Screenshot showing a created member for a structure.":::

1. Open the column's shortcut menu, and select **Properties**. Provide values for each member's properties based on the following table:

   | Property | Description or value |
   |----------|----------------------|
   | **Data Type** | .NET data type for the member |
   | **Error Handling** | Trigger an error, round, or truncate. |
   | **Host Data Type** | The member's COBOL or RPG data type |
   | **Name** | The member's name |
   | **Precision** | The member's data precision |
   | **Trailing filler** | For members where the length is less than the specified maximum, you must specify the filler size. |

### Add a union

1. In the main design view, open the **Unions** shortcut menu, and select **Add Union**.

   :::image type="content" source="media/la-newproject-add-union1.png" alt-text="Screenshot showing main design view, Unions shortcut menu, and selected option for Add Unions.":::

   The designer creates a union with two members. 

1. To add another member, open the new union's shortcut menu, and select **New Member**. Repeat this step as necessary.

1. Provide the following information for each member:

   | Property | Description or value |
   |----------|----------------------|
   | **Is Array** | If true, you must set the array dimensions, which support arrays with up to 7 dimensions and 16,777,215 elements. You must also enter values for the array properties **Occurs Count In** and **Occurs Depending On**. |   
   | **Data Type** | The .NET data type for the member. This value can include structures defined in the previous section. |
   | **Name** | The member's name |
   | **Error Handling** | Trigger an error, round, or truncate. |
   | **Host Data Type** | The member's COBOL or RPG data type |
   | **Precision** | The member's data precision |
   | **Trailing filler** | For members where the length is less than the specified maximum, you must specify the filler size. |

1. When you're done, continue to the next section to create the library that stores the metadata's design.

## Create the Host Integration Definition XML (HIDX) or metadata artifact

1. To generate the metadata artifact, on the Visual Studio **File** menu or toolbar, select **Save All**. (Keyboard: Press Ctrl+Shift+S)

   :::image type="content" source="media/la-newproject-add-saveall.png" alt-text="Screenshot showing Visual Studio toolbar with selection option for Save All.":::

1. To find the generated HIDX file, go to your host application's directory.

   :::image type="content" source="media/la-newproject-output-hidx.png" alt-text="Screenshot showing Visual Studio Output window with HIDX file location.":::

## Related content

- [Importing Host Definitions](application-integration-importhostdefs.md)
