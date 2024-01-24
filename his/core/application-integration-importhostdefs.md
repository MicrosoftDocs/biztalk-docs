---
title: Import COBOL host definitions
description: Learn how to import COBOL host definitions for CICS, IMS, and host files.
ms.service: host-integration-server
ms.topic: how-to
ms.date: 10/31/2023
---

# Import COBOL host definitions for CICS, IMS, and host files

The original Host Integration Server TI Designer feature was introduced with the full capabilities for designing metadata artifacts from scratch with the assistance from a mainframe programmer. Later, the capability to import host definitions in COBOL or RPG copybook format was added to support scenarios for automating design and reducing involvement from mainframe programmers. Over the years, this capability became the principal option to create metadata artifacts.

## Prerequisites

- [Download and install Visual Studio](https://visualstudio.microsoft.com/downloads/). After installation, make sure that you also install the workload named **Desktop development with C++ in Visual Studio**. Otherwise, you get the error **Exception from HRESULT 0x800A007C**.

- [Download and install the HIS Designer for Azure Logic Apps](https://aka.ms/his-designer-logicapps-download). The only prerequisite is [Microsoft .NET Framework 4.8](https://aka.ms/net-framework-download).

- A Visual Studio [host application solution and project (CICS or IMS](application-integration-lahostapps.md) or [host file solution project](application-integration-lahostfiles.md) where you want to import the host definition.

  > [!NOTE]
  >
  > The HIS Designer provides and shows different options based on whether you open a CICS, IMS, or host file solution.

- Understand how the programming model works for the technology that you want to integrate, which is CICS or IMS. Both platforms have different requirements and ways to pass and receive information. Make sure that you learn about the appropriate [programming model](choosing-the-appropriate-programming-model1.md) before you import the host definitions.

- Obtain the host definitions (copybooks) that you want to import into HIS Designer for Logic Apps. This designer supports COBOL and RPG copybooks.

## Prepare a COBOL copybook

- COBOL copybooks should follow the basic COBOL coding rules. The HIS Designer for Logic Apps enforces many of those rules. The following table lists the main rules:

   | Columns | Type | Observation |
   |---------|------|-------------|
   | 1–6 | Sequence number | Don't enter anything in these positions. |
   | 7 | Indicator | Use an asterisk (*) or slash (/) to code a comment. |
   | 8-11 | A Margin (Area A) | 77 level numbers and 01 level numbers |
   | 12-72 | B Margin (Area B) | Reserved for 02 levels and higher |
   | 73-80 | Identification | No definitions are allowed here. |

- Verify that the COBOL or RPG copybook meets the requirement of the selected [programming model](choosing-the-appropriate-programming-model1.md).

- Verify the dots at the end of every line. Make sure they appear, even though COBOL's latest versions don't require this formatting.

- If your copybook includes REDEFINEs, have the mainframe programmer confirm the host definition that you want to use, if no discriminant is available.

- Remove any character other than the ones stated in the earlier table. Make sure that you have the correct number of characters.

## Import a COBOL host definition (CICS)

The following steps show how to import a COBOL copybook for a CICS host application project into the HIS Designer for Logic Apps. This COBOL program follows the CICS ELM Link [programming model](choosing-the-appropriate-programming-model1.md).

1. In Visual Studio, open the CICS host application solution, which automatically opens the HIS Designer for Logic Apps.

1. In the designer's left pane, open the component node's shortcut menu, and select **Import** > **Host Definition**.

   In the following example, the component node is named **NetCInt1**.

   :::image type="content" source="media/la-newproject-import-hostdef1.png" alt-text="Screenshot shows Visual Studio, HIS design view, and NetCInt1 component node shortcut menu with Import, Host Definition selected.":::

1. In the **Import System z COBOL Source File** box, select **Browse**.

   :::image type="content" source="media/la-newproject-import-hostdef2.png" alt-text="Screenshot shows Import System Z COBOL Source File box for CICS.":::

1. Find and select the copybook to import, and then select **Open**.

   :::image type="content" source="media/la-newproject-import-hostdef3.png" alt-text="Screenshow shows the file explorer and a selected copybook to use for a CICS host application.":::

   The following example shows the COBOL program to import:

   ```  
      *****************************************************************
      ** THIS PROGRAM IS A SAMPLE CICS SERVER THAT DEMONSTRATES A      *
      ** SIMPLE BANKING APPLICATION WHICH FORMATS AND RETURNS AN      *
      ** ARRAY OF ACCOUNT RECORDS THAT WILL CONTAIN EITHER CHECKING OR*
      ** SAVINGS INFORMATION.                                         *
      *****************************************************************
       IDENTIFICATION DIVISION.
       PROGRAM-ID. GETAINFO.
       ENVIRONMENT DIVISION.

       DATA DIVISION.

      *****************************************************************
      ** VARIABLES FOR INTERACTING WITH THE TERMINAL SESSION          *
      *****************************************************************
       WORKING-STORAGE SECTION.

       LINKAGE SECTION.

       01 DFHCOMMAREA.
          05 SSN                          PIC X(9).
          05 ACCT-ARRAY OCCURS 2 TIMES.
             10 ACCT-NUM                  PIC X(10).
             10 ACCT-TYPE                 PIC X.
             10 ACCT-INFO                 PIC X(39).
             10 CHECKING REDEFINES ACCT-INFO.
                15 CHK-OD-CHG             PIC S9(3)V99   COMP-3.
                15 CHK-OD-LIMIT           PIC S9(5)V99   COMP-3.
                15 CHK-OD-LINK-ACCT       PIC X(10).
                15 CHK-LAST-STMT          PIC X(10).
                15 CHK-DETAIL-ITEMS       PIC S9(7)      COMP-3.
                15 CHK-BAL                PIC S9(13)V99  COMP-3.
             10 SAVINGS  REDEFINES ACCT-INFO.
                15 SAV-INT-RATE           PIC S9(1)V99   COMP-3.
                15 SAV-SVC-CHRG           PIC S9(3)V99   COMP-3.
                15 SAV-LAST-STMT          PIC X(10).
                15 SAV-DETAIL-ITEMS       PIC S9(7)      COMP-3.
                15 SAV-BAL                PIC S9(13)V99  COMP-3.
                15 FILLER                 PIC X(12).

       PROCEDURE DIVISION.
           IF SSN = '111223333' THEN
      **********************************************************
      *   SSN = 111223333 IS AN INDICATION TO RETURN A
      *   DISCRIMINATED UNION OF CHECKING AND SAVINGS ACCOUNTS
      **********************************************************
              MOVE 'CHK4566112' TO ACCT-NUM         OF ACCT-ARRAY(1)
              MOVE 'C'          TO ACCT-TYPE        OF ACCT-ARRAY(1)
              MOVE SPACES       TO ACCT-INFO        OF ACCT-ARRAY(1)

              MOVE 25.00        TO CHK-OD-CHG       OF ACCT-ARRAY(1)
              MOVE 2000.00      TO CHK-OD-LIMIT     OF ACCT-ARRAY(1)
              MOVE 'SAV1234567' TO CHK-OD-LINK-ACCT OF ACCT-ARRAY(1)
              MOVE '10/31/2005' TO CHK-LAST-STMT    OF ACCT-ARRAY(1)
              MOVE 1            TO CHK-DETAIL-ITEMS OF ACCT-ARRAY(1)
              MOVE 41852.16     TO CHK-BAL          OF ACCT-ARRAY(1)

              MOVE 'SAV1234567' TO ACCT-NUM         OF ACCT-ARRAY(2)
              MOVE 'S'          TO ACCT-TYPE        OF ACCT-ARRAY(2)
              MOVE SPACES       TO ACCT-INFO        OF ACCT-ARRAY(2)
              MOVE 4.50         TO SAV-INT-RATE     OF ACCT-ARRAY(2)
              MOVE 5.00         TO SAV-SVC-CHRG     OF ACCT-ARRAY(2)

              MOVE '10/15/2005' TO SAV-LAST-STMT    OF ACCT-ARRAY(2)
              MOVE 1            TO SAV-DETAIL-ITEMS OF ACCT-ARRAY(2)
              MOVE 146229.83    TO SAV-BAL          OF ACCT-ARRAY(2)
           ELSE
      **********************************************************
      *   SSN = 333221111 IS AN INDICATION TO RETURN A
      *   SIMPLE REDEFINITION OF CHECKING ACCOUNTS ONLY
      **********************************************************
              MOVE 'CHK4566112' TO ACCT-NUM         OF ACCT-ARRAY(1)
              MOVE 'C'          TO ACCT-TYPE        OF ACCT-ARRAY(1)
              MOVE SPACES       TO ACCT-INFO        OF ACCT-ARRAY(1)

              MOVE 25.00        TO CHK-OD-CHG       OF ACCT-ARRAY(1)
              MOVE 2000.00      TO CHK-OD-LIMIT     OF ACCT-ARRAY(1)
              MOVE 'SAV1234567' TO CHK-OD-LINK-ACCT OF ACCT-ARRAY(1)
              MOVE '10/31/2005' TO CHK-LAST-STMT    OF ACCT-ARRAY(1)
              MOVE 1            TO CHK-DETAIL-ITEMS OF ACCT-ARRAY(1)
              MOVE 41852.16     TO CHK-BAL          OF ACCT-ARRAY(1)

              MOVE 'CHK7896112' TO ACCT-NUM         OF ACCT-ARRAY(2)
              MOVE 'C'          TO ACCT-TYPE        OF ACCT-ARRAY(2)
              MOVE SPACES       TO ACCT-INFO        OF ACCT-ARRAY(2)

              MOVE 25.00        TO CHK-OD-CHG       OF ACCT-ARRAY(2)
              MOVE 2000.00      TO CHK-OD-LIMIT     OF ACCT-ARRAY(2)
              MOVE 'SAV7891234' TO CHK-OD-LINK-ACCT OF ACCT-ARRAY(2)
              MOVE '10/31/2005' TO CHK-LAST-STMT    OF ACCT-ARRAY(2)
              MOVE 1            TO CHK-DETAIL-ITEMS OF ACCT-ARRAY(2)
              MOVE 41852.16     TO CHK-BAL          OF ACCT-ARRAY(2)
           END-IF.

           EXEC CICS RETURN END-EXEC.
   ```

1. Review the copybook to import. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef4.png" alt-text="Screenshot shows the Import System z COBOL Source File box with the selected and preloaded host definition for CICS.":::

1. After the **Item Options** box opens and populates with the artifact name and the **Link-to-Program name** value, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef5.png" alt-text="Screenshot shows Item Options box to select item type, such as Method, Data Table, Structure, or Union for CICS.":::

   The designer presents the metadata artifact that's generated from the COBOL copybook.

   :::image type="content" source="media/la-newproject-import-hostdef6.png" alt-text="Screenshot shows metadata artifact design view for CICS in the HIS Designer.":::

   The designer also generates a host definition for the copybook. This host definition doesn't include the entire provided copybook, but only the fields and datatypes needed for the artifact to interact with the mainframe program. Although the previously provided sample is an entire program, the HIS Designer extracts only the information required based on the selected [programming model](choosing-the-appropriate-programming-model1.md).

   :::image type="content" source="media/la-newproject-import-hostdef7.png" alt-text="Screenshot shows parsed host definition view for CICS in HIS Designer.":::

1. To generate the HIDX, select **Save All**.

   :::image type="content" source="media/la-newproject-add-saveallhf.png" alt-text="Screenshot shows Visual Studio toolbar with Save All selected.":::

1. To find the generated HIDX file, go to your host application's folder.

## Import a COBOL host definition (IMS)

Both CICS and IMS host mission-critical programs, but each have different requirements. The following steps show how to import a COBOL copybook for an IMS host application project into the HIS Designer for Logic Apps. This COBOL program follows the IMS Connect [programming model](choosing-the-appropriate-programming-model1.md).

1. In Visual Studio, open the IMS host application solution, which automatically opens the HIS Designer for Logic Apps.

1. In the designer's left pane, open the component node's shortcut menu, and select **Import** > **Host Definition**.

   In the following example, the component node is named **NetCInt1**.

   :::image type="content" source="media/la-newproject-import-hostdef1.png" alt-text="Screenshot shows Visual Studio, HIS design view, and the NetCInt1 component node shortcut menu with Import, Host Definition selected.":::

1. In the **Import System z COBOL Source File** box, select **Browse**.

   :::image type="content" source="media/la-newproject-import-hostdef2.png" alt-text="Screenshot shows Import System Z COBOL Source File box for IMS.":::

1. Find and select the copybook to import, and then select **Open**.

   :::image type="content" source="media/la-newproject-import-hostdef8.png" alt-text="Screenshow shows the file explorer and a selected copybook to use for a IMS host application.":::

   The following example shows the COBOL program to import:

      ```
       IDENTIFICATION DIVISION.
       PROGRAM-ID. GETBAL.
       ENVIRONMENT DIVISION.
   
       DATA DIVISION.
   
       WORKING-STORAGE SECTION.
      **************************************************************
      * USER DATA DEFINITIONS.                                     *
      **************************************************************
   
       01  INPUT-AREA.
           05  LLI                      PIC S9(4) COMP VALUE ZERO.
           05  ZZI                      PIC S9(4) COMP VALUE ZERO.
           05  TRAN                     PIC X(7) VALUE SPACES.
           05  NAME                     PIC X(30).
           05  ACCNUM                   PIC X(6).
   
       01  OUTPUT-AREA.
           05  LLO                      PIC S9(4) COMP VALUE ZERO.
           05  ZZO                      PIC S9(4) COMP VALUE ZERO.
           05  ACCBAL                   PIC S9(7)V9(2) COMP-3.
   
       01  IMS-VALUES.
           02  END-OF-MSG               PIC X(2)       VALUE 'QD'.
           02  QUEUE-EMPTY              PIC X(2)       VALUE 'QC'.
           02  GU                       PIC X(4)       VALUE 'GU  '.
           02  ISRT                     PIC X(4)       VALUE 'ISRT'.
           02  CHNG                     PIC X(4)       VALUE 'CHNG'.
   
       LINKAGE SECTION.
       01  IOTP-PCB.
           05  IOTP-LTERM                           PIC X(8).
           05  FILLER                               PIC X(2).
           05  IOTP-STATUS                          PIC X(2).
           05  IOTP-PREFIX.
               10  IOTP-DATE                        PIC S9(7) COMP-3.
               10  IOTP-TIME                        PIC S9(7) COMP-3.
               10  IOTP-MSG-NUMBER                  PIC S9(4) COMP.
               10  FILLER                           PIC X(2).
           05  IOTP-MOD-NAME                        PIC X(8).
           05  IOTP-USER-ID                         PIC X(8).
   
       PROCEDURE DIVISION.
           ENTRY 'DLITCBL' USING IOTP-PCB.
           CALL 'CBLTDLI' USING GU IOTP-PCB INPUT-AREA.
   
              IF IOTP-STATUS = END-OF-MSG
                 DISPLAY 'IOTP-STATUS = END-OF-MSG'
              END-IF.
              IF IOTP-STATUS = QUEUE-EMPTY
                 DISPLAY 'IOTP-STATUS = QUEUE-EMPTY'
              END-IF.
              IF IOTP-STATUS NOT = ' '
                 DISPLAY 'CALL FAILED IOTP-STATUS = ' IOTP-STATUS
              END-IF.
   
           MOVE 777.12               TO ACCBAL OF OUTPUT-AREA.
   
           MOVE LENGTH OF OUTPUT-AREA TO LLO.
           CALL 'CBLTDLI' USING ISRT IOTP-PCB OUTPUT-AREA.
              IF IOTP-STATUS NOT = ' '
                 DISPLAY 'SEND FAILED IOTP-STATUS = ' IOTP-STATUS
              END-IF.
   
           GOBACK.
   ```

1. Review the copybook to import. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef9.png" alt-text="Screenshot shows the Import System z COBOL Source File box with the selected and preloaded host definition for IMS.":::

1. After the **Item Options** box opens and populates with the artifact name and the **Transaction ID** value, select **Next**.

   > [!NOTE]
   >
   > For the next steps, confirm that the **Use Importer defaults** option isn't selected or available,
   > which should be the default behavior when you're working with an IMS host application.

   :::image type="content" source="media/la-newproject-import-hostdef10.png" alt-text="Screenshot shows Item Options box to select item type, such as Method, Data Table, Structure, or Union for IMS.":::

1. After the **Input Area** box opens, select all the items in the **INPUT AREA** node, and then select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef11.png" alt-text="Screenshot shows the Input Area box for the IMS host transaction.":::

1. After the **Output Area** box opens, select all the items in the **OUTPUT AREA** node, and then select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef12.png" alt-text="Screenshot shows the Output Area box for the IMS host transaction.":::

1. After the **Return Value** box opens, select an item in the **OUTPUT AREA** node for the return value, and then select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef13.png" alt-text="Screenshot shows the Return Value box for the IMS host transaction.":::

1. After the **Data Tables, Structures and Unions** box opens, select the groups to use for the data tables and structures, and then select **Next**.

   This example doesn't require any selections, so no items are selected.

   :::image type="content" source="media/la-newproject-import-hostdef14.png" alt-text="Screenshot shows Data Tables, Structures, and Unions box for IMS.":::

1. After the **LL Fields Area** box opens, select the LL fields that must be excluded from the transaction. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef15.png" alt-text="Screenshot shows the LL Fields Area box for IMS.":::

1. After the **ZZ Fields Area** box opens, select the ZZ fields that must be excluded from the transaction. When you're ready, select **Next**.

   :::image type="content" source="media/la-newproject-import-hostdef16.png" alt-text="Screenshot shows the ZZ Fields Area box.":::

1. After the **TRANCODE Fields Area** box opens, select the TRANCODE fields that must be excluded from the transaction. When you're ready, select **Finish**.

   :::image type="content" source="media/la-newproject-import-hostdef17.png" alt-text="Screenshot shows the TRANCODE Fields Area box.":::

   The designer shows the metadata artifact generated from the COBOL copybook:
   
   :::image type="content" source="media/la-newproject-import-hostdef18.png" alt-text="Screenshot shows metadata artifact design view for IMS in the HIS Designer.":::
   
   The designer also generates a host definition for the copybook. This host definition doesn't include the entire provided copybook, but only the fields and datatypes needed for the artifact to interact with the mainframe program. Although the previously provided sample is an entire program, the HIS Designer extracts only the information required based on the selected [programming model](choosing-the-appropriate-programming-model1.md).
   
   :::image type="content" source="media/la-newproject-import-hostdef19.png" alt-text="Screenshot shows parsed host definition view for IMS in HIS Designer.":::

1. Select **Save All** to generate the HIDX.

   :::image type="content" source="media/la-newproject-add-saveallhf.png" alt-text="Screenshot shows Visual Studio toolbar with Save All selected.":::

1. To find the generated HIDX file, go to your host application's folder.

## Import a COBOL host file definition (Host files)

IBM host files have multiple types and can exist in mainframes or midrange systems. Each have their own types and characteristics. The demand is increasing to modernize or migrate mainframe and midrange applications that use host file data. One example is migrating virtual storage access method (VSAM) files to Azure. With this demand, the use case is becoming more common to access and integrate these files into modern solutions.

The following steps show how to import a COBOL copybook for a host file project into the HIS Designer for Logic Apps. This COBOL copybook represents a simple VSAM file. The import wizard creates structures and unions. After you import the copybook, you can create and assign tables to the correct schemas.

1. In Visual Studio, open your host file solution, which automatically opens the HIS Designer for Logic Apps.

1. the designer's left pane, open the component node's shortcut menu, and select **Import** > **Host Definition**.

   In the following example, the component node is named **HostFileDefinition1**.

   :::image type="content" source="media/la-newproject-import-hostdefhf1.png" alt-text="Screenshot shows Visual Studio, HIS design view, and the HostFileDefinition1 component node shortcut menu with Import, Host Definition selected.":::

1. In the **Import System z COBOL Source File** box, select **Browse**.

   :::image type="content" source="media/la-newproject-import-hostdefhf2.png" alt-text="Screenshot shows Import System Z COBOL Source File box for a host file.":::

1. Find and select the copybook to import, and then select **Open**.

   :::image type="content" source="media/la-newproject-import-hostdefhf3.png" alt-text="Screenshow shows the file explorer and a selected copybook to use for a host file.":::

   The following example shows the COBOL program to import:

   ```
         ******************************************************************        
         *HIS TRANSACTION DESIGNER EXPORT, 9.0
         *DATA DECLARATION GENERATED ON 9/23/2013 5:21:51 PM
         ******************************************************************        
         *LIBRARY NAME.............CustomerDatabaseZOS.HIDX
         *DESCRIPTION..............NONE AVAILABLE
         ******************************************************************        
          01  CUSTOMER-RECORD.
              05 CUSTOMER-NAME               PIC X(30).
              05 CUSTOMER-SSN                PIC X(9).
              05 CUSTOMER-ADDRESS.
                 10 CUSTOMER-STREET          PIC X(20).
                 10 CUSTOMER-CITY            PIC X(10).
                 10 CUSTOMER-STATE           PIC X(4).
                 10 CUSTOMER-ZIP             PIC 9(5).
              05 CUSTOMER-PHONE              PIC X(13).
              05 CUSTOMER-ACCESS-PIN         PIC X(4).
   ```  
 
1. In the **Import System z COBOL Source File** box, review the copybook to import.

1. Confirm that the selections for the following options for the host definition: **REDEFINE**, **Use Importer defaults**, and **Generate structure on indents**. When you're ready, select **Next**. 

   :::image type="content" source="media/la-newproject-import-hostdefhf4.png" alt-text="Screenshot shows the Import System z COBOL Source File box with the selected and preloaded host definition for a host file.":::

   The designer shows the metadata artifact generated from the COBOL copybook. This artifact is incomplete, so you must create one or more tables that reflect the host file.

   :::image type="content" source="media/la-newproject-import-hostdefhf6.png" alt-text="Screenshot shows the metadata artifact view in HIS Designer for a host file.":::

1. In the component node tree, open the **Tables** shortcut menu, and select **Add Table**.

   :::image type="content" source="media/la-newproject-import-hostdefhf7.png" alt-text="Screenshot shows artifact design view and the open Tables shortcut menu with Add Table selected.":::

1. Open the new table's shortcut menu, and select **Properties**. In the **Properties** window, update the following properties:

   | Property | Description |
   |----------|-------------|
   | **Alias** | The table name, for example, **CUSTOMER** |
   | **Host File Name** | The mainframe or midrange system name for the host file, for example, **HISDEMO.NWIND.CUSTOMER** |
   | **Schema** | The previously imported schema, for example, **CUSTOMER_RECORD** |

   The following example shows the updated table properties:

   :::image type="content" source="media/la-newproject-import-hostdefhf8.png" alt-text="Screenshot shows table properties window with Alias, Host File Name, and Schema properties.":::

   The following example shows the completed host file's metadata artifact:

   :::image type="content" source="media/la-newproject-import-hostdefhf9.png" alt-text="Screenshot shows completed metadata artifact in HIS Designer for a host file.":::

1. To generate the HIDX. file, select **Save All**.

   :::image type="content" source="media/la-newproject-add-saveallhf.png" alt-text="Screenshot shows Visual Studio toolbar with Save All selected.":::

1. To find the generated HIDX file, go to your host application's folder.
